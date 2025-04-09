---
tags: python
---
{%hackmd r-DeEzFISrGDUrAsdxJDjA %}

# Übung 12: Objektorientierung

## Klasse `Schueler` erstellen

1. Ein Schüler verfügt über eine Methode `gruessen`, die den Text `Hallo` ausgibt.
2. Ein Schüler wird mit Vorname, Nachname und Geburtsdatum erstellt. Implementieren Sie dazu einen passenden Konstruktor.
3. Ergänzen Sie den Konstruktor um die automatische Generierung eines Benutzernamens: Der Benutzername besteht aus dem ersten Buchstaben des Vornamens und bis zu sieben Buchstaben des Nachnamens.

**Hinweis:** Für die folgenden Aufgaben sind magische Methoden erforderlich.

4. Zwei Schüler gelten als gleich (`__eq__`), wenn ihre Benutzernamen identisch sind.
5. Die Funktion `repr(hans)` soll einen String liefern, der den Schüler als Python-Code exakt rekonstruieren kann.
6. Die Funktion `str(hans)` soll eine benutzerfreundliche Darstellung des Schülers mit allen relevanten Attributen zurückgeben.
7. Bei jeder Erstellung eines Schülers soll ein Zähler erhöht werden.
8. Lagern Sie die Generierung des Benutzernamens in eine statische Methode `benutzername_generieren` aus.



## Klasse `Schulklasse`

1. Der Konstruktor erhält die Klassenbezeichnung als Argument.
2. Über die Methode `add_schueler` können Schüler zur Klasse hinzugefügt werden.
3. Beim Hinzufügen soll automatisch im Schülerobjekt vermerkt werden, welcher Klasse er zugeordnet ist.
4. Ein Schüler kann über die Methode `austreten()` die Klasse verlassen – dabei wird er automatisch aus der Klassenliste entfernt.

##### Beispieldaten

```python
b10a = Schulklasse("b10a")
b10a.add_schueler(Schueler("Adam", "Bauer", "Gestern"))
b10a.add_schueler(Schueler("Cindy", "Dammböck", "Gestern"))
b10a.add_schueler(Schueler("Emil", "Fuhr", "Gestern"))
b10a.add_schueler(Schueler("Gerda", "Hummel", "Gestern"))
b10a.add_schueler(Schueler("Ingo", "Jäger", "Gestern"))
b10a.add_schueler(Schueler("Katrin", "Lang", "Gestern"))
b10a.add_schueler(Schueler("Marco", "Nussbaum", "Gestern"))
```



## Serialisierung einer Schulklasse

1. Der Konstruktor der Klasse `Schulklasse` soll ein optionales Argument `schueler` akzeptieren, um beim Erzeugen direkt eine Schülerliste mitzugeben.
2. Implementieren Sie `repr(b10a)`, sodass die Schulklasse als String serialisiert werden kann.
3. Testen Sie:
   - Erzeugen Sie `b10a` mit Beispielschülern.
   - Fügen Sie einen weiteren Schüler hinzu.
   - Speichern Sie die Repräsentation in eine Datei:

     ```python
     with open('serialisierte_klasse.txt', 'w') as file:
         file.write(repr(b10a))
     ```

   - Lesen Sie die Datei ein und erzeugen Sie die Objektstruktur neu.



## Information Hiding

1. Übersetzen Sie das folgende Java-Programm in idiomatisches Python. Verwenden Sie `@property` und `@setter`, wo sinnvoll.
2. Erstellen Sie eine vereinfachte Version der Klasse, in der auf die Zählung der Namensänderungen verzichtet wird.
   ```java
   public class Haustier{
    
      private String name;
      private int namen_geaendert = 0;
      
      public String getName() {
          return this.name;
      }
      
      public int getAenderungen() {
          return this.namen_geaendert;
      }
      
      public void setName(String name) {
          this.name = name;
          this.namen_geaendert++;
      }
	  
	  public void Haustier(String name) {
	      this.name = name
	  }
	  
	  public void koten() {
	      return "AA"
	  }
  
      public static void main(String []args){
          Haustier bello = new Haustier("Bella");
          bello.setName("Bello");
          System.out.println(bello.getName());
          System.out.println(bello.getAenderungen());
      }
   }
   ```
2. Verzichten Sie auf das Zählen der Namensänderung und geben Sie eine API-kompatible Kurzform der Klasse an.

## Vererbung

1. Erstellen Sie eine Klasse `Katze`, die von `Haustier` erbt und eine Methode `miauen` besitzt.
2. Prüfen Sie: Werden Konstruktoren in Java, C# und Python vererbt? (Tipp: siehe Skript)
3. Erzeugen Sie eine Katze.
4. Überprüfen Sie mit `isinstance`, ob die Katze ein Haustier ist.
5. Überschreiben Sie die Methode `koten`, sodass `"Katzen-AA"` zurückgegeben wird.
6. Verwenden Sie `super()`, um die `koten`-Methode der Basisklasse in der neuen `koten`-Methode aufzurufen, und erweitern Sie die Rückgabe zu `"Katzen-" + Superkoten`.
   
  
ChatGPT zur Vererbung. Stimmt das so?
> In C#, Java und Python werden Konstruktoren nicht direkt vererbt. Ein Konstruktor ist eine spezielle Methode, die verwendet wird, um ein Objekt einer Klasse zu initialisieren. Wenn eine Klasse in C#, Java oder Python von einer anderen Klasse erbt, erbt sie die Eigenschaften und Methoden der Basisklasse, jedoch nicht den Konstruktor selbst.
> 
> Wenn eine abgeleitete Klasse erstellt wird, kann sie den Konstruktor der Basisklasse aufrufen, um die Initialisierung der vererbten Eigenschaften durchzuführen. Dies geschieht normalerweise mithilfe des Schlüsselworts "super" in Java und Python oder des Schlüsselworts "base" in C#. Durch den Aufruf des Konstruktors der Basisklasse wird sichergestellt, dass die Initialisierung der vererbten Eigenschaften korrekt durchgeführt wird.
> 
> Es ist wichtig zu beachten, dass eine abgeleitete Klasse keinen direkten Zugriff auf den Konstruktor der Basisklasse hat, sondern nur den Aufruf des Konstruktors in der eigenen Konstruktorimplementierung ermöglicht. Der Konstruktor der Basisklasse wird also nicht direkt vererbt, sondern kann von der abgeleiteten Klasse aufgerufen werden, um die Initialisierung der vererbten Eigenschaften zu ermöglichen.**
   
## Mehrfachvererbung

1. Erstellen Sie die Klasse `Schmusbar`.
   - Sie besitzt ein Attribut `streicheleinheiten`, das bei jedem Aufruf von `schmusen()` um 1 erhöht wird.
   - Der Konstruktor ohne Argumente initialisiert `streicheleinheiten` mit 0.
2. Erstellen Sie die Klasse `Kuscheltier`.
3. `Kuscheltier` ist weder `Haustier` noch umgekehrt. Aber eine `Katze` ist sowohl ein `Haustier` als auch `schmusbar`. Lassen Sie `Katze` von beiden Klassen erben.
   - Welcher Konstruktor wird aufgerufen?
   - Die Katze muss einen Namen haben und `streicheleinheiten` korrekt initialisieren. Rufen Sie beide Konstruktoren explizit auf.


<!--
```python 
class Haustier1:

    def __init__(self, name):
        self.__name = name
        self.__namen_geaendert = 0

    @property
    def name(self):
        return self.__name

    @name.setter
    def name(self, name):
        self.__name = name
        self.__namen_geaendert += 1

    @property
    def aenderungen(self):
        return self.__namen_geaendert

    def koten(self):
        return "AA"

class Haustier:

    def __init__(self, name):
        self.name = name

    def koten(self):
        return "AA"

class Schmusbar:

    def __init__(self):
        self.__streicheleinheiten = 0

    def schmusen(self):
        self.__streicheleinheiten += 1

    @property
    def streicheleinheiten(self):
        return self.__streicheleinheiten

class Kuscheltier:
    pass

class Katze(Haustier, Schmusbar):

    def __init__(self, name = "Mimi"):
        super().__init__(name)
        Schmusbar.__init__(self)

    def miauen(self):
        return "miau"

    def koten(self):
        return "Katzen-" + super().koten()
        # return "Katzen-" + Haustier.koten(self)


if __name__ == '__main__':
    bello = Haustier("ballasd")
    print(bello.name)
    bello.name = "Bello"
    bello.name = "Bello"
    print(bello.name)
    # print(bello.aenderungen)

    kitty = Katze("Kitty")
    print(kitty.name)
    kitty.schmusen()
    kitty.schmusen()
    print(kitty.streicheleinheiten)
    print(isinstance(kitty, Haustier1))
```

-->

## Weitere Übung (Mitarbeiter)


1. Definieren Sie eine Klasse Mitarbeiter. Ein Mitarbeiter besitzt
eine eindeutige Nummer `id` und einen Namen `name`.

   1. Die ID des Mitarbeiters soll durch die Klasse selbst fortlaufend nummeriert
werden. Der erste Mitarbeiter hat also die ID 1, der zweite Mitarbeiter die ID 2 usw.
   1. Überlegen Sie sich für `id` und `name`, ob einfache Attribute genügen oder ein Property sinnvoll wäre. Und implementieren Sie es so.
   2. Der Code `print(hans)` soll die Ausgabe `Mitarbeiter: Hans Gruber (5)` ausgeben. Implementieren Sie die entsprechende magische Methode
   3. Fügen Sie eine Statische Methode `to_name()` hinzu, die zu einem gegebenen Mitarbeiter den Namen zurückgibt. Kennzeichnen Sie die Methode als statisch.
  
2. Schreiben Sie eine Klasse `PersonalVerwaltung`.
   1. Diese Klasse
hat eine Mitarbeiterliste. (readonly)
   2. Mitarbeiter können im Konstruktor direkt als Liste, Menge oder Tupel übergeben werden.
   2. und auch Methoden zum Hinzufügen und zum
Entfernen von Mitarbeitern. 
   3. Außerdem benötigt sie eine Methode `list_mitarbeiter()`, um alle Mitarbeiter auf der Konsole
auszugeben.
 
   3. Fügen Sie der Klasse `PersonalVerwaltung` eine Methode
`sort_mitarbeiter()` hinzu. Diese Methode soll die Mitarbeiter sortieren. Das funktioniert für eine Liste `l` mit `l.sort(key=Mitarbeiter.to_name)`

4. Lassen Sie die Klasse `GeordnetePersonalVerwaltung` von der `PersonalVerwaltung` erben. Die `GeordnetePersonalVerwaltung` ist so implementiert, dass die Mitarbeiter automatisch nach jeder Änderung sortiert werden.
   1. Versuchen Sie dabei, so oft wie möglich die Fuktionalität der Superklasse zu verwenden.
   1. Weiterhin solll die die Klasse `GeordnetePersonalVerwaltung` von der Klasse
      ```python 
      class Stringable:
	     def __str__(self):
		    return str(self.__dict__)
      ```
      erben. (Soll aber nur verwendet werden, wenn `PersonalVerwaltung` kein `__str__()` hat.)
   2. Implementieren für `PersonalVerwaltung` ein `__str__()` und testen Sie noch mal welches von `GeordnetePersonalVerwaltung` verwendet wird.
5. Implementieren Sie eine Klasse `Abrechnung` mit einem readolny-Property `periode` und einem readonly-`mitarbeiter`. Auch die Periode wird automatisch fortlaufend nummeriert.
6. Lassen Sie die Klassen `GehaltsAbrechnung` und `LohnAbrechnung` von `Abrechnung` erben.
   1. Eine Lohnabrechnung wird mit den Werten mitarbeiter, sundenlohn und stunden initialisiert.
   2. Eine `Gehaltsabrechnung` mit den Argumenten mitarbeiter, gehalt.
   3. Implementieren Sie für beide Abrechnungen ein read-only `verdienst`-Property. 

<!--

```python 
class Mitarbeiter:
    __staticid = 0

    def __init__(self, name):
        Mitarbeiter.__staticid += 1
        self.name = name
        self.__id = Mitarbeiter.__staticid

    @property
    def id(self):
        return self.__id

    def __str__(self):
        return "Mitarbeiter: " + self.name + "(" + str(self.id) + ")"

    @staticmethod
    def to_name(mitarbeiter):
        return mitarbeiter.name


class PersonalVerwaltung:

    def __init__(self, mitarbeiter=[]):
        self.__mitarbeiterliste = []
        for m in mitarbeiter:
            self.__mitarbeiterliste.append(m)

    def __str__(self):
        return ("__str__ von Personalverwaltung")

    @property
    def mitarbeiterliste(self):
        return self.__mitarbeiterliste

    def add_mitarbeiter(self, mitarbeiter):
        self.__mitarbeiterliste.append(mitarbeiter)

    def remove_mitarbeiter(self, mitarbeiter):
        self.__mitarbeiterliste.remove(mitarbeiter)

    def list_mitarbeiter(self):
        for m in self.__mitarbeiterliste:
            print(m)

    def sort_mitarbeiter(self):
        self.__mitarbeiterliste.sort(key=Mitarbeiter.to_name)


class Stringable:
    def __str__(self):
        return str(self.__dict__)


class GeordnetePersonalVerwaltung(PersonalVerwaltung, Stringable):
    def add_mitarbeiter(self, mitarbeiter):
        super().add_mitarbeiter(mitarbeiter)
        self.sort_mitarbeiter()


class Abrechnung:
    __periodenzaehler = 0

    def __init__(self, mitarbeiter):
        Abrechnung.__periodenzaehler += 1
        self.__periode = Abrechnung.__periodenzaehler
        self.__mitarbeiter = mitarbeiter

    @property
    def mitarbeiter(self):
        return self.__mitarbeiter
    
    @property
    def periode(self):
        return self.__periode

    @property
    def verdienst(self):
        raise Exception("Kein Verdienst")

    def __str__(self):
        return self.mitarbeiter.name


class Gehaltsabrechnung(Abrechnung):

    def __init__(self, mitarbeiter, gehalt):
        super().__init__(mitarbeiter)
        self.__gehalt = gehalt

    @property
    def verdienst(self):
        return self.__gehalt


class LohnAbrechnung(Abrechnung):

    def __init__(self, mitarbeiter, stundenlohn, stunden):
        super().__init__(mitarbeiter)
        self.__stundenlohn = stundenlohn
        self.__stunden = stunden

    @property
    def verdienst(self):
        return self.__stundenlohn * self.__stunden

hans = Mitarbeiter("Hans")
egon = Mitarbeiter("Egon")
#g = Gehaltsabrechnung(hans, 2000)
g = LohnAbrechnung(egon, 12, 150)
print(g.mitarbeiter)
print(g.verdienst)
```
-->

## Corona

<!-- Verbesserung: Bessere Integration von Stat und Tageswert -->

Entscheiden Sie jeweils selbst ob Sie ein Property oder ein Attribut verwenden.

1. Ein Landkreis hat einen Namen und eine Einwohnerzahl. Die sollen im Konstruktor  gesetzt werden. Es sind Abfragen und Änderungen nachträglich möglich. Wenn die Einwohnerzahl geändert soll allerdings geprüft werden, ob es sich ob es sich um einen `int` handelt.
2. Erstellen Sie den "Demolandkreis" mit 200000 Einwohnern.
3. Geben Sie den "Demolandkreis" mit `print()` am Bildschirm aus. Dazu müssen Sie eine magische Methode schreiben. Verwenden sie heute `__repr__`

5. Erstellen Sie eine Klasse Tageswert, der die Anzahl der Neuinfektionen `anz` das Datum `datum` und den Landkreisnamen `lk_name` als Eigenschaften hat.
6. Spicken Sie https://docs.python.org/3/library/datetime.html#examples-of-usage-date und
   1. Generieren Sie sich ein date-Objekt mit dem aktuellen Datum und
   2. erstellen Sie ein en Tageswert mit diesem Datum.
   3. Geben Sie den Tageswert mit `print()` nach dem Beispiel `Demolandkreis 2021-02-08 300` aus.
6. Erstellen Sie eine Klasse Statistik. Diese entzhält (Singleton Pattern) eine statische Methode `get_instance` um die einzige Instanz dieser Klasse zu bekommen. (Properties gibt es nur von Objekten, nicht von Klassen)
   1. Das erzeugen weiterer Instanzen soll eine Fehlermeldung erzeugen. ()
   2. Die Klasse Enthält eine Liste von Landkreisen, welche zunächst leer ist. Außerdem enthält sie eine private Liste, die für jeden Landkreis ein Dictionary enthält, das einem Datum einen bestimmten Wert zuteilt.
   3. Erstellen Sie eine Methode `add_lk`, die einen Landkreis hinzufügt. (Die Methode muss beide Listen anpassen)
   4. Erstellen Sie eine Methode `add_wert` Das einen Tageswert in das entsprechende Dictionary einfügt. Dazu wird neben dem Tageswert ein Index übergeben.
   5. Erstellen Sie die magische Methode `__getitem__` ein Tupel mit Landkreis und zugehörigen Tageswerten zurückgibt.
   6. Warum ist die Methode magisch. Wie könnten wir sie implizit aufrufen?
   
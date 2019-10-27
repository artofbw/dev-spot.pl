---
title: Programowanie obiektowe w Pythonie 3
date: "2019-10-17T23:12:32.169Z"
template: "post"
draft: false
slug: "/posts/programowanie-obiektowe-w-pythonie-3/"
category: "Python 3"
tags:
  - "#Programowanie"
  - "#Python3"
  - "#Naukaprogramowania"
  - "#Programming"
description: "W sposób podstawowy opowiadam o programowaniu obiektowym w języku Python 3. Dowiedz się czym jest Klasa i jak utworzyć jej obiekt oraz w jaki sposób zadeklarować atrybut, czy metodę."
socialImage: "/media/python-logo.png"
---

![](/media/python-logo.png)

Niezwykle kluczowym elementem programowania są **klasy** oraz **obiekty**. 
W tym wpisie zaprezentuję Ci **podstawy** dotyczące **programowania obiektowego**. 

Czego dowiesz się po przeczytaniu tego artykułu? :

+ Czym jest **klasa** a czym **obiekt**?
+ Kiedy warto korzystać z klas i programować obiektowo - mocne i słabe strony?
+ Czym są pola i metody.
+ Jak stworzyć **klasę** i jej konstruktor

![](/media/How_To_Do_Object_Oriented_Programming_The_Right_Way.png)

## Klasa
Klasa jest strukturą utworzoną przez użytkownika, w której zawarte są wszystkie jej **atrybuty** oraz **metody**. 
Jest swego rodzaju szablonem tego, co chcemy zaprezentować w instancji obiektu.


```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def be_awesome(self):
        print(self.name + " is being awesome.")

```

## Kiedy chcemy programować obiektowo?
Na wstępie warto powiedzieć, że programować obiektowo można zawsze. Natomiast czy warto? 
**TAK**, ale przy większych projektach, pomoże to w zachowaniu schludnej struktury projektu.
Warto też choćby dla samego treningu. W innym wypadku, programowanie obiektowe (OOP), jeśli projekt ma np. 100-200 linii kodu
okaże się to przerostem formy nad treścią i w zupełności wystarczy nam kilka funkcji.
## Obiekt

Utworzony na podstawie klasy, zwany również często **instancją** klasy. 
Jest to istniejący byt, który posiada zainicjowane atrybuty oraz zachowania (metody).

```python
john = Person(name="John", age=33)
```

Powyżej przykład zainicjowanej klasy, do której możemy się odwoływać za pomocą zmiennej `john`

## Metody

Najprościej mówiąc metoda jest **funkcją** z tym, że znajduje się ona w obrębie **klasy** - czyli, są ze sobą powiązane.
Metody można podzielić na **metody klasy** oraz **metody magiczne** zaczynające się o dwóch podkreślników, o tych drugich więcej przyszłości lub w dokumentacji -
[Special method names](https://docs.python.org/3/reference/datamodel.html#special-method-names)

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def __str__(self):
        return self.name
        
    def get_age(self):
        return f"I'm {self.age} years old."
```
```
john = Person(name="John", age=33)
>>> john.__str__()
'John'
>>> john.get_age()
"I'm 33 years old."
```

## Pola
To atrybuty klasy, czyli np. `self.name`, `self.age`. 
Są `zmiennymi` składowymi klasy, co oznacza że możesz je odczytywać i modyfikować. 
Wszystkie informacje dotyczące danej klasy, które jesteś w stanie opisać jak np.:

+ imię
+ nazwisko
+ wiek
+ wysokość
+ waga
+ itp. itd.

![](/media/python-oop-meme.jpg)

## Tworzenie klasy i Konstruktora
Tworzenie klas w Pythonie jest tak naprawdę banalnie proste, 
a możliwości są niemal nieograniczone. 
Rozbudujmy naszą klasę `Person` odrobinę o imię i nazwisko, wiek, wysokość i wagę oraz przywitajmy się, czy policzmy nasze BMI(Body Mass Index)
Zobacz jak wygląda to w praktyce.

```python
class Person:
    def __init__(self, first_name, last_name, age, height, weight):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age
        self.height = height
        self.weight = weight
        
    def __str__(self):
        return self.name
        
    def greetings(self):
        return f"Hi!"
        
    def get_full_name(self):
        return f"{self.first_name} {self.last_name}"
        
    def get_age(self):
        return f"I'm {self.age} years old."
        
    def calculate_body_mass_index(self):
        height = self.height
        return self.weight // (height * height);
```
```
>>> john = Person(first_name="John", last_name="Smith", age=50, height=1.88, weight=100)
>>> john.greetings()
'Hi!'
>>> john.get_full_name()
>>> john.get_age()
"I'm 50 years old."
>>> john.calculate_body_mass_index()
28.0
```

## Podsumowanie

Umiesz już tworzyć i rozwijać **klasy**, a także utworzyć jej obiekt. 
Możliwości Pythona są zdecydowanie bardziej złożone, ale pozwala Ci to na zabawę z programowaniem obiektowym i dalszy rozwój.

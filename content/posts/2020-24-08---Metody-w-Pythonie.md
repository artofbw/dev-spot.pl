---
title: Metody regularne vs klasowe vs statyczne
date: "2020-08-24T21:44:32.169Z"
template: "post"
draft: false
slug: "/posts/metody-w-pythonie/"
category: "Python 3"
tags:
  - "#Programowanie"
  - "#Python3"
  - "#Naukaprogramowania"
  - "#Programming"
  - "#Rekrutacja"
  - "#MetodyPython"
description: "Jakie metody można deklarować w Pythonie - w praktyczny sposób dowiesz się o metodzie regularnej, klasy oraz statycznej. Językiem laika opowiem o różnicach dla wcześniej wspomnianych metod."
socialImage: "/media/python-logo.png"
---

![](/media/python-logo.png)

Niejednokrotnie osoby początkujące, często też osoby bardziej doświadczone mają problem ze zrozumienień dekoratorów `@classmethod` oraz `@staticmethod`. 
Te różnicę warto znać, szczególnie że na rekrutacjach technicznych często pojawia się pytanie odnośnie ich znajomości. Poniżej przygotowałem **klasę** zawierającą metody w różnych wariantach. Na tej podstawie będę starał podzielić się ten wpis na użycie tych metod na opcję z zainicjowanym obiektem oraz na samej klasie.

Czego dowiesz się po przeczytaniu tego artykułu? :

+ Jak działa metoda **regularna**, **klasowa** oraz **statyczna**.
+ Kiedy powinno się ich używac.

```python
class Methods:
    first_name = 'John'

    def regular_method(self):
        print("Hi,", self.first_name)
    
    def regular_method_with_param(self, last_name):
        print("Hi,", self.first_name, last_name)
    
    @classmethod
    def class_method(cls):
        print("Hi,", cls.first_name)
    
    @classmethod
    def class_method_with_param(cls, last_name):
        print("Hi,", cls.first_name, last_name)
    
    @staticmethod
    def static_method():
        print("Printing static method")
    
    @staticmethod
    def static_method_with_param(param):
        print("Printing parameter:", param)
        

# Testy dla instancji klasy    
methods = Methods()

methods.regular_method()
methods.regular_method_with_param('Doe')
methods.class_method()
methods.class_method_with_param('Doe')
methods.static_method()
methods.static_method_with_param('Doe')


# Testy dla klasy

Methods.regular_method()
Methods.regular_method_with_param('Doe')
Methods.class_method()
Methods.class_method_with_param('Doe')
Methods.static_method()
Methods.static_method_with_param('Doe')

```

## Testy dla instancji klasy

1. Pierwsza metoda `methods.regular_method()` zadziała ze względu że posiadamy instancję klasy `methods` - inaczej by nie zadziałało, zwróci `Hi, John`.
2. `methods.regular_method_with_param('Doe')`, jak wyżej - dodatkowo przekazujemy parametr do metody - zwróci `Hi, John Doe`.
3. `methods.class_method()` - zwróci `Hi, John`.
4. `methods.class_method_with_param('Doe')` - jak wyżej, tyle że przekazujemy dodatkowy parametr.
5. `methods.static_method()` - wyświetli `Printing static method` - metoda statyczna zadziała z instancją klasy czy też na samej klasie.
6. `methods.static_method_with_param('Doe')` - identycznie jak wyżej - tyle, że z dodatkowym paramterem

## Testy dla klasy

1. `Methods.regular_method()` - tu pierwszy raz spotykamy się z czymś nowym - zwrotka to `regular_method() missing 1 required positional argument: 'self'`. Wywołanie metody regularnej (czy też metody instancji - różnie ludzie nazywają) wymaga stworzenia instancji obiektu.
2. `Methods.regular_method_with_param('Doe')` - tutaj otrzymamy `regular_method_with_param() missing 1 required positional argument: 'last_name'`, ale to dlatego, że `Doe` chce wejść w miejsce parametru `self`.
3. `Methods.class_method()` - wyświetli `Hi, John`. Przy `@classmethods` nie potrzebujemu tworzyć instancji obiektu, aby ją wyświetlić - to właśnie ich zaleta.
4. `Methods.class_method_with_param('Doe')` - tak samo, jak w przykładzie powyżej, dodatkowo przekazujemy parametr.
5. `Methods.static_method()` - Zostanie wywołana i zwróci `Printing static method`. Działa dla obu przypadków.
6. `Methods.static_method_with_param('Doe')` - jak wyżej.


## Podsumowanie
- Metody regularne działają tylko dla instancji klasy.
- `@classmethod oraz @staticmethod` działają zarówno dla instancji klasy jak i samej klasy.
- `@classmethod` posiada dostęp do zmiennej klasy `cls`, której `@staticmethod` nie posiada.

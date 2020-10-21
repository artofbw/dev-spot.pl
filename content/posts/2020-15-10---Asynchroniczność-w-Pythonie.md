---
title: Asynchroniczny Python
date: "2020-08-24T21:44:32.169Z"
template: "post"
draft: false
slug: "/posts/asynchroniczny-python/"
category: "Python 3"
tags:
  - "#Programowanie"
  - "#Python3"
  - "#Naukaprogramowania"
  - "#Programming"
  - "#AsyncAwait"
  - "#Asynchroniczność"
description: "Asynchroniczny kod - Jak to działa? O co w tym chodzi?."
socialImage: "/media/python-logo.png"
---

![](/media/python-logo.png)

`Async` i `Await` to słowa kluczowe wprowadzona od Pythona 3.5+. Jakie różnice są między kodem synchronicznym a asynchronicznym? Językiem laika postaram się to objaśnić.

Czego dowiesz się po przeczytaniu tego artykułu? :

+ Różnice w sync vs async.
+ Słowa kluczowe.
+ Przykład implementacji kodu asynchronicznego.

## Różnice
Słowem wstępu o różnicach, które idealnie przedstawia poniższy obrazek, zaciągnięty z internetu.

![](https://lh3.googleusercontent.com/proxy/Z4YQfrotUvs6bwNGzmaUTxZQTNYdUlH76z2sSOd-CbxQTxbM7Q3SXlrI3B6M8Q-s3Pd-iS1cTJxrcs-5q4U0QxBCZFTn6Cu6KZFkjgUz910XEsDJspk52hDVGTSVt8C-rcSrMIfLb9sa12blSIQ)

Opisując - wyobraźcie sobie, że macie do wykonania aplikację typu proxy - taką która będzie tłumaczyła interesujące nas dane z jakiegoś API, dla klienta który chce te dane skonsumować w oczekiwanej dla niego strukturze.
Klient ma do dyspozycji całą masę endpointów i oczekuję, że komunikacja będzie pracowała bez problemu. 
Wysyłając do nas request w wersji synchronicznej musi spodziewać się, że nasz request będzie czekał na response. 
Natomiast w weresji asynchronicznej może wysłać dowolną ilość requestów, a responsy przyjdą jak będą już gotowe.


## Słowa kluczowe

1. `async` oraz `await` to słowa kluczowe w kodzie asynchronicznym Pythona.
2. `Coroutine` to funkcja, która ma funkcję zawieszenia, wznowienia lub przeniesienia wykonywania do innego programu.
3. `Event loop` (Pętla zdarzeń) - Jest odpowiedzialny za uruchamianie i zarządzanie koroutynami oraz callbacki.
4. `Asyncio` - To biblioteka wspierająca `async/await` w Pythonie.


## Przykład

Poniżej prosty przykład

```python
import asyncio

async def witaj():
    print('Witaj ...')
    await asyncio.sleep(2)
    print('... czytelniku')
    
asyncio.run(witaj())
```

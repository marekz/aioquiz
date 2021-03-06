Listy zakupów
====================================

Python ma pięć podstawowych typów danych:
- Liczba
- String
- Lista
- Tupla
- Słownik

Używaliśmy już liczb (całkowitych int i zmiennoprzecinkowych float), stringów i tupli. Nadszedł czas, by poznać
listy i słowniki.

'Słodki Kłólik'

Dziewczynka idzie do sklepu ze zwierzątkami domowymi i pyta o kłólika.
Sprzedawca pochyla się nad nią, uśmiecha i pyta:

"Chciałabyś ślicznego puszystego białego króliczka, 
czy słodkiego kudłatego brązowego króliczka?"

"Właściwie", odpowiada dziewczynka, "Nie sądzę, by mój pyton zauważył różnicę."

A teraz wracajmy do nauki :)

Lista
=====

Nie wspomnieliśmy dotychczas o listach, bo nie różnią się one od intuicyjnej
koncepcji list znanej z codziennego życia. Możemy myśleć o listach w Pythonie
tak samo, jak myślimy o każdej innej liście (liście zakupów, liście gości,
wynikach egzaminu itd.) spisanej na papierze i ponumerowanej.

Zacznijmy od czystej strony w interpreterze Pythona:

```python
>>> L = [] 
>>> L
```

W każdej chwili możemy sprawdzić, ile elementów przechowujemy w liście,
stosując funkcję len:

```python
>>> len(L) 
0
```

Stwórzmy kolejną listę (o takiej samej lub innej, niż poprzednia lista nazwie):

```python
>>> L = ["Ala", "Ola", "Jacek"] 
>>> len(L)
3
```

Tak, jak w przypadku tupli, kolejne elementy listy są oddzielone przecinkami. 
Zaś w odróżnieniu od tupli, nawiasy `[` i `]` są obowiązkowe.

Dostęp do wartości w liście
---------------------------

Tak możemy wyświetlić określony element listy (pamiętajcie, że liczymy od zera):

```python
>>> L = ["Ala", "Ola", "Jacek"] 
>>> L[0]
'Ala'
>>>  L[1]
'Ola' 
>>> L[2] 
'Jacek' 
>>>  L[3]
Traceback (most recent call last): File "<stdin>", line
1, in <module> IndexError: list index out of range
```

Możemy również użyć pętli, by wykonać instrukcję dla każdego elementu
listy:

```python
>>>  for imię in L: 
 ... print ("Imię:", imię) 
Imię: Ala
Imię: Ola 
Imię: Jacek
```

W ten sam sposób możemy wydrukować pierwszą część choinki bożonarodzeniowej:

```python
>>>  lista = [1, 2, 3] 
>>> for n in lista: 
... print("*"*n)
```

Podstawowe operacje na listach
------------------------------

Listy reagują na operatory + i \* podobnie, jak stringi. Znaki te oznaczają
również tutaj konkatenację (łączenie tekstów) i powtórzenie, ale rezultatem
jest lista, a nie string.

Okazuje się, listy reagują na wszystkie ogólne operacje dla sekwencji, które
używalismy na stringach w poprzednim rozdziale.

```python
>>>  len([1, 2, 3])   # Długość 
>>> [1, 2, 3] + [4, 5, 6]     # Konkatenacja
[1, 2, 3, 4, 5, 6]
>>>  ['Hi!'] * 4    # Powtórzenie 
['Hi!', 'Hi!', 'Hi!', 'Hi!']
>>>  3 in [1, 2, 3]   # Zawieranie się 
True 
>>> L = ["Ala", "Ola", "Jacek"] 
>>> L[1] 
'Ola'
>>>  L[-1] 
'Jacek' 
>>> L[1:] 
['Ola', 'Jacek'] 
>>>  L[:1] 
['Ala'] 
>>> L[1:2] 
['Ola'] 
>>>  L[1:3] # komenda L[3] wywoła błąd! 
['Ola', 'Jacek']
```

Range (Zakres)
--------------

Cóż, niestety ciągle musimy sami pisać całą zawartość listy. Ten problem
może być rozwiązany dzięki użyciu funkcji range. Wypróbuj komendę
`help(range)`, aby zapoznać się z wszystkimi możliwościami funkcji range lub wykonaj
tych kilka przykładów: 

```python
>>>  list(range(2)) 
[0, 1] 
>>> list(range(1, 11))
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 
>>> list(range(1, 11, 2))
[1, 3, 5, 7, 9]

```python
for i in range(10):
    print(i)

    print(i)

```

Aktualizowanie list
-------------------

Możesz zmienić jeden lub wiele elementów listy poprzez wybranie elementu,
który chcesz zmienić i nadanie mu nowej wartości. Możesz również dodawać do listy
nowe elementy używając metody append().

```python
>>>  lista = ['fizyka', 'chemia', 1997, 2000\]
>>>  print(lista[2]) 
>>>  lista[2] = 2001
>>>  print(list[2])

>>>  lista_2 = ['a', 'b'] 
>>>  lista_2.append('c')
>>>  print(lista_2)
```

Usuwanie elementów listy
------------------------

Aby usunąć element z listy, możesz użyć komendy del, jeśli wiesz dokładnie,
który element chcesz usunąć lub metody remove(), jeśli tego nie wiesz.
Na przykład:

```python
>>>  lista1 = \['fizyka', 'chemia', 1997, 2000\]
>>>  print(lista1) 
>>>  del lista1[2]
>>>  print(lista1)
```

Tuple
=====

Na początku wspomnieliśmy, że nie możemy używać przecinków w liczbach,
bo będziemy potrzebowali ich w tuplach. Doszliśmy właśnie do tego
momentu:

```python
>>>  1, 2, 3
(1, 2, 3)
>>> ("Ala", 15)
('Ala', 15)
>>>  x = 1,5
>>> print(x)
(1, 5)
```

Tupla to nic innego, jak zbiór kilku wartości. Wartości te odddzielamy
przecinkami. Zbiór najczęściej otaczamy nawiasami zwykłymi, ale nie jest to
konieczne. Chyba, że chcemy objąć zbiorem zero elementów (jakkolwiek
dziwnie to może brzmieć):

```python
>>> ()
()
```

Tuple możemy łączyć:

```python
>>> nazwy = ("Paulina", "Kowalska")
>>> szczegóły = (27, 1.70)
>>> nazwy + szczegóły
('Paulina', 'Kowalska', 27, 1.7)
```

Możemy w nich także zawrzeć inne tuple, np. punkty na mapie możemy
zgrupować następująco:

```python
>>>  punkt = ("Nazwa punktu", (x, y))
```

gdzie `x` i `y` to liczby.

Możemy odwoływać się do tak zgrupowanych wartości poprzez ich kolejną
pozycję w tupli (zaczynając od zera), np.:

```python
>>> p = (10, 15)
>>> p[0] # pierwsza wartość
10
>>> p[1] # druga wartość
15
```

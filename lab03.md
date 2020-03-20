# Wstęp

Wiele zjawisk biologicznych czy ekonomicznych można wymodelować probabilistycznie. Polega to na odpowiednim wyborze modelu (np. rozkładu teoretycznego). Modelowanie tych zjawisk oraz rozkłady teoretyczne opierają się na rachunku prawdopodobieństwa.


# Podstawowe pojęcia w rachunku prawdopodobieństwa

### Zad. 1

Gdy rzucasz kostką do gry, **zmienna losowa** to liczba wyrzuconych oczek. 

**Zdarzenie losowe** polega na otrzymaniu jednej spośród sześciu możliwych wartości tej zmiennej. 

Pojedynczy wynik doświadczenia (np. wypadnięcie szóstki) nazywamy **zdarzeniem elementarnym**. 

Zbiór wszystkich możliwych wyników doświadczenia losowego nazywamy **przestrzenią zdarzeń elementarnych** i oznaczamy dużą grecką literą omega Ω 

```
Ω = {1, 2, 3, 4, 5, 6}
```

### Zad. 2
Zdarzenia elementarne przyjęło się oznaczać wielkimi literami z początku alfabetu (A,B,C). Na przykład zdarzenie elementarne polegające na wyrzuceniu pięciu lub sześciu oczek w rzucie kostką zapiszemy: 

```
A = {5, 6}
```

Zatem prawdopodobieństwo trafienia piątki lub szóstki zapiszemy jako: 

```
P(A) = |A| / |Ω| = 2 / 6 = 0.33
```

Zdarzenia, których prawdopodobieństwo otrzymania wynosi 1 nazywają się zdarzeniami pewnymi. Z kolei, zdarzenia, których prawdopodobieństwo wynosi 0 nazywają się zdarzeniami niemożliwymi.

## Dyskretne rozkłady prawdopodobieństwa
W dyskretnych rozkładach prawdopodobieństwa zmienna losowa przyjmuje skończony zbiór wartości w przedziale liczbowym (np. liczba oczek na kostce, liczba dzieci, liczba pomyłek). Jest to zmienia skokowa, która najczęściej zmienia się o jeden.

### Zad. 3
Ile wynosi prawdopodobieństwo wypadnięcia orła dokładnie dwa razy?
> O: orzeł, R: reszka

Ω = {OOO, **OO**R, ORO R**OO**, RRO, ROR, ORR, RRR}

```
P(X = 2) = 3/8
```

### Zad. 4
Samodzielnie

### Zad. 5
Podczas trzech rzutów monetą prawdopodobieństwo:
- wypadnięcia orła 0 razy: P(X = 0) = 1/8 
- wypadnięcia orła 1 raz: P(X = 1) = 3/8
- wypadnięcia orła 2 razy: P(X = 2) = 3/8
- wypadnięcia orła 3 razy: P(X = 3) = 1/8

Prawdopodobieństwa zdarzeń elementarnych muszą się sumować do 1.

```R
x = c(0, 1, 2, 3)
y = c(1/8, 3/8, 3/8, 1/8)
plot(x, y)
plot(x, y, type="h")
barplot(y, names.arg = x)
```

### Zad. 6
Prawdopodobieństwo, że orzeł wypadnie przynajmniej jeden raz:

```
P(X >= 1) = 3/8 + 3/8 + 1/8 = 7/8
```

### Zad. 7
Wartość oczekiwana liczby wypadnięć orła to:

```
E(X) = 0 * 1/8 + 1 * 3/8 + 2 * 3/8 + 4 * 1/8
```

W R:

```R
sum(x*y)
```

Szybsze rozwiązanie: liczba rzutów *n* razy prawdopodobieństwo wypadnięcia orła.

```
E(X) = n * p = 3 * 0.5
```


### Zad. 8
Rzucam 5 razy kostką do gry i chciałbym wiedzieć jakie jest prawdopodobieństwo, że szóstka wypadnie dokładnie dwa razy. Zamiast wypisywać wszystkie kombinacje zdarzeń elementarnych (Ω = {11111, 11112, ..}), korzystamy z rozkładu dwumianowego.

Rozkład ten opisuje prawdopodobieństwo zajścia *k* sukcesów w ciągu *n* niezależnych prób (zdarzeń losowych), z których każda próba ma stałe prawdopodobieństwo sukcesu równe *p*. Innymi słowy, o tym rozkładzie mówimy wtedy, kiedy mamy *n* niezależnych doświadczeń losowych (np. 3 rzuty monetą), w których prawdopodobieństwo sukcesu (zajścia określonego zdarzenia np. wypadnięcia orła) w każdym doświadczeniu jest stałe i niezależne od wyników poprzednich i równe *p* (np. wynosi 0.5).

Funkcję prawdopodobieństwa otrzymania dokładnie *k* sukcesów na *n* prób określa wzór Bernouliego.

<img src="https://latex.codecogs.com/svg.latex?\Large&space;x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" title="\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" />

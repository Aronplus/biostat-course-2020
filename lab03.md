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

# Dyskretne rozkłady prawdopodobieństwa
W dyskretnych rozkładach prawdopodobieństwa zmienna losowa przyjmuje skończony zbiór wartości w przedziale liczbowym (np. liczba oczek na kostce, liczba dzieci, liczba pomyłek). Jest to zmienia skokowa, która najczęściej zmienia się o jeden.

## Rozkład dwumianowy
Używamy tego rozkładu, kiedy w wyniku możemy otrzymać dwie wartości (np. sukces-porażka, zdrowy-chory, orzeł-reszka, puryna-pirymidyna).

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

<img src="https://latex.codecogs.com/png.latex?%5Clarge%20P%28X%20%3D%20k%29%20%3D%20P%28k%2C%20n%2C%20p%29%20%3D%20%7Bn%20%5Cchoose%20k%7Dp%5E%7Bk%7D%281-p%29%5E%7B%7Bn-k%7D%7D%5C%21" title="P(X = k) = P(k, n, p) = {n \choose k}p^{k}(1-p)^{{n-k}}\!" />

Obliczmy prawdopodobieństwo wypadnięcia 2 orłów w trzech rzutach monetą.

<img src="https://latex.codecogs.com/png.latex?%5Clarge%20P%28X%20%3D%202%29%20%3D%20P%282%2C%203%2C%200.5%29%20%3D%20%7B3%20%5Cchoose%202%7D0.5%5E%7B2%7D%20%5Ccdot%200.5%5E%7B%7B1%7D%7D%5C%21%20%3D%200.375" title="P(X = 2) = P(2, 3, 0.5) = {3 \choose 2}0.5^{2}  \cdot 0.5^{{1}}\! = 0.375" />

W programie R jest funkcja `dbinom`, która oblicza prawdopodobieństwo jeżeli podamy *k*, *n* i *p*.

```R
> dbinom(2, 3, 0.5)            # Funkcja prawdopodobieństwa
[1] 0.375                      # Prawdop. wypadnięcia orła dokładnie 2 razy.
```

Jakie jest prawdopodobieństwo, że orzeł wypadnie przynajmniej raz?

```R
> dbinom(1:3, 3, 0.5)
[1] 0.375 0.375 0.125          # Prawdop. wypadnięcia orła 1, 2 i 3 razy  
> sum(dbinom(1:3, 3, 0.5))     # Suma wartości tych prawdopodobieństw
[1] 0.875
```

Ile zatem wynosi prawdopodobieństwo, że w 5 rzutach kostkach, szóstka wypadnie dokładnie dwa razy?


### Zad. 9
samodzielnie

### Zad. 10
samodzielnie

### Zad. 11
samodzielnie

### Zad. 12
Koszykarz oddaje 4 rzuty do kosza. Piłka wpada do kosza z prawdopodobieństwem 0.8. Oblicz: 

1. wartość prawdopodobieństwa celnych rzutów do kosza (0, 1, 2, 3, 4)

   ```R
   dbinom(0:4, 4, 0.8)
   ```
2. wartość oczekiwaną celnych rzutów do kosza

   ```R
   4 * 0.8       # E(X) = n * p
   ```

   lub:

   ```R
   x = 0:4
   y = dbinom(x, 4, 0.8)
   sum(x * y)
   ```

3. wartość prawdopodobieństwa, że koszykarz trafi celnie co najwyżej 3 razy.

   ```R
   sum(dbinom(0:3, 4, 0.8))
   ```
   
   lub

   ```R
   pbinom(3, 4, 0.8)   # Dystrybuanta. Odpowiada ona na pytanie ile wynosi 
                       # prawdop. znalezienia wartości mniejszej bądź równej
                       # od danej wartości X 

   ```

### Zad. 13
samodzielnie

### Zad. 14
samodzielnie

### Zad. 15
samodzielnie

### Zad. 16
Wyświetl rozkład dwumianowy w R.

```R
library("TeachingDemos")              # Załaduj pakiet
install.packages("TeachingDemos")     # Zainstaluj pakiet (jeżeli niezainstalowany)
vis.binom()
```

Gdy *p* jest większe niż 0.5 to rozkład jest lewoskośny (długi lewy ogon), gdy mniejsze to prawoskośny (długi prawy ogon).

## Rozkład Poissona
Drugim popularnym typem dyskretnego rozkładu prawdopodobieństwa jest rozkład Poissona. Rozkład ten jest często nazywany rozkładem zdarzeń rzadkich. Tak więc przykłady zmiennych o rozkładzie Poissona to: liczba wypadków na osobę, liczba wygranych w totolotku, liczba awarii występujących w procesie produkcyjnym, liczba zwierząt na pewnym terenie. Te liczby są zgodne z rozkładem Poissona. 

Rozkładu Poissona używamy, kiedy nie jesteśmy w stanie określić, ile maksymalnie zajść zdarzenia może wystąpić w pewnym czasie *t*. W przeciwieństwie do rozkładu dwumianowego, gdzie zlicza się liczbę sukcesów i porażek, w rozkładzie Poissona liczy się jedynie zajście zdarzenia.

Funkcja prawdopodobieństwa ma postać:

<img src="https://latex.codecogs.com/png.latex?%5Clarge%20P%28X%3Dk%29%20%3D%20P%28k%2C%20%5Clambda%29%20%3D%20%5Cfrac%7B%5Clambda%5E%7Bk%7D%7D%7Bk%21%7De%5E%7B-%5Clambda%7D%20%3D%20%5Cfrac%7B%28np%29%5E%7Bk%7D%7D%7Bk%21%7De%5E%7B-np%7D" title="P(X=k) = P(k, \lambda) = \frac{\lambda^{k}}{k!}e^{-\lambda} = \frac{(np)^{k}}{k!}e^{-np}" />

Parametr λ jest wartością oczekiwaną (średnią) w tym rozkładzie, natomiast *k* oznacza liczbę zajść pewnego zdarzenia.


### Zad. 17
Dane z zadania:

* λ = 2
* *k* = 3

Obliczenie prawdopodobieństwa wprowadzenia 3 błędnych nukleotydów podczas replikacji DNA człowieka.

<img src="https://latex.codecogs.com/png.latex?%5Clarge%20P%28X%3D3%29%20%3D%20P%283%2C%202%29%20%3D%20%5Cfrac%7B2%5E%7B3%7D%7D%7B3%21%7De%5E%7B-2%7D%20%3D%200.180447" title="P(X=3) = P(3, 2) = \frac{2^{3}}{3!}e^{-2} = 0.180447" />

W R:

```R
> dpois(3, 2)
[1] 0.180447
```

### Zad. 18
Dane z zadania:
* λ = 10000
* k = 10100

```R
sum(dpois(0:10100, 10000))   
```

lub 

```R
ppois(10100, 10000)
```
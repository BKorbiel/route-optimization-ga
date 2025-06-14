# Optymalizacja tras przy użyciu algorytmu genetycznego

Projekt realizowany w ramach kursu akademickiego. Celem projektu było rozwiązanie problemu komiwojażera (TSP) za pomocą algorytmu genetycznego (GA).

## Opis projektu
### Cel projektu
Celem projektu jest zaimplementowanie algorytmu genetycznego (GA), który optymalizuje trasę kuriera odwiedzającego zestaw punktów (wariant problemu komiwojażera – TSP). Celem algorytmu jest znalezienie najkrótszej możliwej trasy przechodzącą przez wszystkie punkty. W ramach projektu przeprowadzono eksperymenty porównujące różne warianty operatorów GA, a także zestawiono skuteczność GA z algorytmem zachłannym (nearest neighbour) i losowym.

### Reprezentacja problemu
- Punkty są rozmieszczone na płaszczyźnie 2D
- Trasa musi wrócić do punktu początkowego (pełny cykl – klasyczny TSP)

### Algorytm genetyczny - szczegóły techniczne
- Reprezentacja chromosomu to permutacja miast (lista indeksów)
- Fitness score jest liczone jako odwrotność długości trasy: `1/total_distance`
- Zastosowano Grid Search do znalezienia najlepszego połączenia funkcji selekcji, funkcji mutacji, funkcji krzyżowania oraz prawdopodobieństwa mutacji
- Rozmiar populacji to 5 * liczba miast
- Algorytm kończy pracę jeżeli nie było poprawy od 100 pokoleń lub po przekroczeniu liczby 3000 pokoleń

Więcej szczegółów odnośnie algorytmu, grid searchu, testowania oraz wyników w pliku route-optimizer.ipynb

## Uruchomienie

### 1. Klonowanie repozytorium

```bash
git clone https://github.com/BKorbiel/route-optimization-ga.git
cd route-optimization-ga
```

### 2. Instalacja zależności

```bash
pip install -r requirements.txt
```

### 3. Uruchomienie notebooka

```bash
jupyter notebook
```

Otwórz plik `route-optimizer.ipynb` - tam znajduje się implementacja algorytmu genetycznego.

## Testowanie

Notebook zawiera komórki testujące działanie algorytmu na różnych instancjach TSP wraz z porównaniem jakości rozwiązania i długości działania z innymi popularnymi algorytmami. Wyniki prezentowane są graficznie oraz liczbowo. Testy potwierdzają, że GA dobrze sobie radzi w znajdowaniu rozwiązań w porównaniu do benchmarków. Jednak ogromną wadą GA jest czas działania.
Więcej szczegółów odnośnie testów i ich wyników oraz śliczne wizualizacje można znaleźć w route-optimizer.ga

## Technologie

- NumPy
- Pandas
- Matplotlib
- Seaborn
- tqdm
- tsplib95

## Struktura projektu

```
route-optimization-ga/
├── tsplib_data/              # Folder na pliki .tsp
├── test_resulst.csv          # Wyniki testów na losowych instancjach
├── tsplib_results.csv        # Syniki testów na instancjach z TSPLIB
├── route-optimizer.ipynb     # Notebook z kodem źródłowym oraz opisem etapów i algorytmu
├── requirements.txt          # Lista zależności
├── README.md                 # Ten plik
└── Raport.pdf                # Raport z projektu
```
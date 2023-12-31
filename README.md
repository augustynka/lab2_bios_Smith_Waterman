**Algorytm Smitha-Watermana
odnoszący się do dopasowań lokalnych w sekwencjach algorytm programowania dynamicznego, który sprawdza optymalne dopasowanie dwóch sekwencji.**

Wykorzystane biblioteki i paczki: **BioPython (SeqIO) oraz os**

**Dane wejściowe:** 
- plik FASTA z rozszerzeniem .fa lub.fasta zawierający dwie sekwencje; 
- wartość gap;
- wartość mismatch; 
- wartość match.

Dane wyjściowe: plik .txt z wynikami dopasowania w formie zmodyfikowanych sekwencji oraz wyniku punktowego.


**Sposób użycia programu:** 

**1.** Uruchom program w terminalu lub interpreterze Pythona.

**2.** Program poprosi o podanie nazwy pliku FASTA zawierającego dwie sekwencje. Plik powinien być w formacie FASTA i posiadać rozszerzenie ".fa" lub ".fasta".

**3.** Jeśli plik o podanej nazwie istnieje, program poprosi Cię o podanie trzech parametrów wartości liczbowych:
- gap
- mismatch
- match

**4.** Program przeprowadzi dopasowanie sekwencji z użyciem algorytmu Smitha-Watermana i zapisze wynik dopasowania i wartość maksymalnego wyniku (score) do pliku "alignment_result.txt". 


**Działanie programu:**
- Podanie nazwy pliku.
- Program weryfikuje poprawność wprowadzonych danych.
- Podanie wartości gap - ilość punktów karnych za przerwę w sekwencji.
- Podanie wartości mismatch - ilość punktów za elementy niedopasowanie w sekwencji.
- Podanie wartości match - ilość punktów za elementy pokrywające się w sekwencji.
- Odczyt z pliku FASTA.
- Sprawdzenie, czy plik zawiera dwie sekwencje
- Przeprowadzenie algorytmu Smith-Waterman:
H i j = max{H i-1, j-1 + s(a i, b j ); H i-k, j - W k ; H i, j-1 - W 1 ;0}

Algorytm działa na macierzy o wymiarach i,j (długości sekwencji), początkowo wypełnionej zerami w pierwszej kolumnie i pierwszym wierszu.

Komórki macierzy wypełniamy maksymalną możliwą wartością, zgodnie ze wzorem:

Mi,j=max{Mi-1,j-1+S-i,yj	Mi-1,j+G	Mi,j-1+G	0}
Sxi,yj - scoring (punktacja za dopasowanie lub niedopasowanie)
G - kara za przerwę


Przykładowa macierz: https://www.researchgate.net/figure/Smith-Waterman-local-alignment-example-A-shows-an-empty-matrix-initialized-for-a_fig2_24309044

Wynikiem pożądanym jest najwyższy możliwy score.




**Przykład użycia** 

Wprowadzenie danych: C:\Users\Patrycja\PycharmProjects\pythonProject\venv\Scripts\python.exe C:\Users\Patrycja\PycharmProjects\pythonProject\main.py 

Podaj nazwę pliku FASTA (z rozszerzeniem fa lub fasta): para_sekwencji.fasta

Podaj wartość gap: 0

Podaj wartość mismatch: -1

Podaj wartość match: 1

Wynik dopasowania zapisany w alignment_result.txt

Przykładowy plik wejściowy:

>1MBO_1|Chain A|MYOGLOBIN|Physeter catodon (9755)
VLSEGEWQLVLHVWAKVEADVAGHGQDILIRLFKSHPETLEKFDRFKHLKTEAEMKASEDLKKHGVTVLTALGAILKKKGHHEAELKPLAQSHATKHKIPIKYLEFISEAIIHVLHSRHPGDFGADAQGAMNKALELFRKDIAAKYKELGYQG

>2MB0_1|Chain A[auth B]|RNA-binding motif protein, X chromosome|Homo sapiens (9606)
MVEADRPGKLFIGGLNTETNEKALEAVFGKYGRIVEVLLMKDRETNKSRGFAFVTFESPADAKDAARDMNGKSLDGKAIKVEQATKPSFESGRRG


Przykładowy plik wyjściowy:

Sekwencja 1: VEAD--VAG-HGQDIL-I--RL--FKSHPET-LEK-FDRFKHLKTEA---EMK-ASEDLKKHG--V-TVLTAL-GAILK--KKGHHE--AELKPLAQS---HA--TKHKIPIKYLEFISEAIIHVLHSRHP-GDFGA-DAQGA--MN-K-AL--ELFRK-DI----A-AK---YKE-LG--YQG

Sekwencja 2: VEADRP--GK-----LFIGG-LNT-----ETN-EKA------L--EAVFG--KY--------GRIVE-VL--LM----KDR-----ETN---K----SRGF-AFVT----------F--E-------S--PA-D--AKDA--ARDMNGKS-LDG----KA-IKVEQAT-KPSF--ES-GRR--G


Max Score: 47


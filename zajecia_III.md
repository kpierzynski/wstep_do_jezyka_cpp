---
marp: true
theme: uncover
class: invert
author: Konrad
---

### Przypomnienie

---

### Tablice

```cpp
char dna[5] = {'T', 'G', 'T', 'A', 'C'};
char dna[] = "TGTAC";

int measurements[] = {1024, 512, 256, 128, 128, 64};
char dna[] = "ATCG";
```

```cpp
char end = '\0';
```

---

### std::string

```cpp
std::string dna = "TCC";

std::cout << dna << " is: " << dna.length() << " chars length." << std::endl;
```

---

# Zajęcia III

---

### Cele:

- zapoznać się z zarządzaniem pamięcią,
- omówić adresy, wskaźniki

---

### Problem

###### (declaration, by_value)

```cpp
#include <iostream>

int number;
void add_5( int x );

int main() {
    add_5( number );
    std::cout << number << std::endl;
    return 0;
}

void add_5( int x ) {
    x = x + 5;
}
```

---

### Problem 2

Napisz funkcję, która policzy i zwróci ilość nukleotydów w ciągu znaków tak, aby funkcja przyjęła argument z ciągiem i zwróciła 4 wartości.

```cpp
int, int, int, int count_nucleotides( std::string dna );
```

---

### Rozwiązanie - wskaźniki 🎉

```cpp
int* a;
```

---

```cpp
int x = 5;
int* pointer_to_x = &x;     // & -> operator pobrania adresu
```

---

```cpp
void swap(int* a, int* b) {
    int tmp = *a;       // * -> operator odczytu wartości
    *a = *b;            // spod adresu (dereferencing operator)
    *b = tmp;
}
```

---

```cpp
#include <iostream>

void swap(int* a, int* b) {
    int tmp = *a;       // * -> operator odczytu wartości
    *a = *b;            // spod adresu (dereferencing operator)
    *b = tmp;
}

int main() {
    int number1 = 10;
    int number2 = 20;

    swap( &number1, &number2 );     // & -> operator pobrania adresu

    std::cout << number1 << " " << number2 << std::endl;
}
```

---

### Arytmetyka wskaźników

```cpp
char dna[] = "ACGT";
char first = *dna;

char second = *(dna+1);
char second = *dna+1;
```

---

### Arytmetyka wskaźników

```cpp
char dna[] = "ACGT";
char first = *dna;

char * original_dna = dna;

char nucleotide1 = *dna++;
char nucleotide2 = *dna++;
char nucleotide3 = *dna++;
```

---

### Arytmetyka wskaźników

```cpp
while(*dna) {
    char nucleotide = *dna++;

    // process nucleotide variable
}
```

---

### Zadanie I

Napisz program, który policzy ilość nukleotydów w ciągu znaków i wypisze ich ilość na wyjście.

- Pamiętaj obsłużyć błędny ciąg. Do tego, stwórz funkcję, która zweryfikuje czy podany ciąg jest
  prawidłowy.
- Musisz w kodzie zawrzeć funkcję o podanej sygnaturze:

---

```cpp
float count_nucleotides( char * dna, int * A, int * T, int * C, int * G)

// return value: percentage of CG nucletides in whole string,
/// e.g. ATTCG should return 40% because there is 2 C's and G's
// and whole string is 5 chars long.

// char * dna: pointer to char array
// int * A, etc: pointers to variables that will store count of nucletides
```

---

### Zadanie II

Napisz program, który wczyta z wejścia ciąg DNA oraz dokona transkrypcji.

- Możesz użyć tylko jednej zmiennej w całym programie, o typie `char dna[]`.
- W programie muszą być co najmniej dwie funkcje. (jedna `main` oraz jedna własna)

---

### Zadanie III

Napisz program, który policzy ilość wystąpień podanego ciągu w ciągu dna.

- Nie korzystaj z `strstr` ani innych typ podobnych, gotowych funkcji do wyszukiwania.
- Musisz skorzystać z wskaźników
- Musisz w kodzie zawrzeć funkcję o podanej sygnaturze:

---

```cpp
int count_substring( char * dna, char * substring )

// return value: number of occurrences of substring in dna

// char * dna: pointer to char array
// char * substring: pointers to variables that will store count of nucletides
```

---

**Przykładowe wejście**:
`"ACGTACGTACGT"`
`"CGT"`

**Przykładowe wyjście**:
`3`

Napisz program tworzący histogram częstości występowania różnych znaków podanych na stdin. Uwaga: łatwiej rysuje się histogram z wykresami poziomymi; pionowa orientacja jest bardziej wymagająca.

```c
#include <stdio.h>
#include <string.h>

void proc_in_stats();

int main()
{
  printf("Enter your text here: ");
  proc_in_stats();
  printf("\n");

  return 0;
}

void proc_in_stats()
{
  int char_count[ 128 ] = { 0 };
  char buff[ 64 ];
  int rv = 0;
  int i;
  size_t j, len;
  for( i = 0 ; i < 5 ; i += 1 ) {
    rv = scanf( "%s", buff );
    if( rv <= 0 ) {
      return;
    }
    else {
      len = strlen( buff );
      for( j = 0 ; j < len ; j += 1 ) {
        char_count[ (int)buff[ j ] ] += 1;
      }
    }
  }
  for( i = 0 ; i < 128 ; i += 1 ) {
    if( char_count[ i ] > 0 ) {
      printf( "\nZnak '%c' wystapil %d razy.", (char)i, char_count[ i ]);
    }
  }
}
```

Trójkąt pitagorejski to trójkąt prostokątny, w którym długość każdego boku jest liczbą całkowitą. Napisz program wypisujący wszystkie trójkąty pitagorejskie, których obwód nie przekracza 1000.

```c
#include<stdio.h>
#include <math.h>

void wypisz_trojkat_pit(double ile);
int czy_calkowita(double a);

int main()
{
    double a;

    a = 1000;
    wypisz_trojkat_pit(a);

    return 0;
}

void wypisz_trojkat_pit(double ile)
{
    double a, b, c, obwod;

    a = 1;

    while ((a * 2) < ile) { 
        b = a;
        obwod = 0;

        while (obwod < ile) {
            c = sqrt(pow(a, 2) + pow(b, 2));
            obwod = a + b + c;

            if (obwod > ile)
                break;

            if (czy_calkowita(c)) {
                printf("%0.0f^2 + %0.0f^2 = %0.0f^2\tOBWÓD:%0.0f\n", a, b,
                       c, obwod);
            }
            ++b;
        }
        ++a;
    }
}


int czy_calkowita(double a)
{
    long long int temp;
    double b;

    temp = (long long int) a;
    b = (double) temp;

    if (a == b)
        return 1;

    return 0;
}
```

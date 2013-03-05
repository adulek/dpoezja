

```c
int main() {
  printf("witaj świecie\n");
}
```

---

Kod programu na użycie liczb double (zmiennych przecinkowych - podwójnej precyzji):

```c
# include <stdio.h>
int main () {
    double a, b;
    a=3.0;
    b=7.0;
    printf("%lf x %lf = %lf \n" ,a, b, a*b);
    printf("%lf - %lf = %lf \n" ,a, b, a-b);
    printf("%lf + %lf = %lf \n" ,a, b, a+b);
    printf("%lf / %lf = %lf \n" ,a, b, a/b);
    getchar();
    return 0;
}
```

Aby wyświetlić odpowiednią ilość miejsc po przecinku wpisujemy w następujący sposób: %. **ilość** lf

---

Kod programu do liczenia długości okręgu i pola koła:


```c
#include <stdio.h>
#include <math.h>
int main () {
    double r;
    printf("Podaj dlugosc promienia:\n");
    scanf("%lf", &r);
    printf("Dlugosc okregu o promieniu %lf wynosi: %lf \n" ,r,2*M_PI*r);
    printf("Pole kola o promieniu %lf wynosi: %lf \n" ,r,M_PI*r*r);
    getchar();
    getchar();
    return 0;
}
```
Trzeba użyć 2 razy:

```c
getchar(); 
getchar();
```

ponieważ pierwszy znak jest pobierany jako enter przechowywany w buforze po wpisaniu promienia.

```c
#include <math.h> 
```

dodaje funkcje matematyczne (np. wartość pi, którą wywołujemy jako M_PI).
Także można użyć:
```c
puts("Podaj dlugosc promienia:")
```
-działa tylko do napisów.

---
Kod programu przeliczającego temperatury (skal Celsjusza i Fahrenheita) -działający w pętli while:

```c
#include <stdio.h>
int main () {
    int fahr, celsius;
    int lower, upper, step;
    lower=0;
    upper=300;
    step=20;
    fahr=lower;
    while(fahr<=upper) {
                       celsius=5*(fahr-32)/9;
                       printf("%d \t %d \n", fahr, celsius);
                       fahr=fahr+step;
                       }
    getchar();
    return 0;
}
```
\t -znak tabulacji.

Zmienienie programu w taki sposób, aby temperatura w Celsjuszach była przeliczana i wyświetlana do 2 miejsca po przecinku:

```c
#include <stdio.h>
int main () {
    double celsius, fahr;
    int lower, upper, step;
    lower=0;
    upper=300;
    step=20;
    fahr=lower;
    while(fahr<=upper) {
                       celsius=5*(fahr-32)/9;
                       printf("%.0lf \t %.2lf \n", fahr, celsius);
                       fahr=fahr+step;
                       }
    getchar();
    return 0;
}
```

czasami trzeba pamiętać, aby liczby wpisywać w następujący sposób 9.0, a nie 9 itd.<br>
Wynik działania jest typu takiego, jakiego była najbardziej zprecyzowana liczba w działaniu.<br>
Sposób wyświetlania %5.1lf oznacza, że liczba będzie wyświetlona na 5 polach z dokładnością do 1 miejsca po przecinku<br>
<br><br><br>

Przerobienie kodu programu na pętlę for:

```c
#include <stdio.h>
#define LOWER 0
#define UPPER 300
#define STEP 20
int main() {
    int fahr;
    for(fahr=LOWER;fahr<=UPPER;fahr=fahr+STEP)
    printf("%3d %6.1lf \n", fahr, (5.0/9.0)*(fahr-32));
    getchar();
    return 0;
}
```
Przy czym:
```c
#define LOWER 0
```
stałe preprocesora -pamiętać, aby nie używać średnika!

---

Kod programu obliczający ciąg Fibonacciego (pętla do-while):

```c
#include <stdio.h>
int main()
{
      int u1, u2, u3; /*na kolejne wyrazy ciągu*/
      int n;          /*numer wyrazu*/
      int i;          /*licznik*/
      
      do {
          printf("Podaj numer wyrazu (co najmniej 3):");
          scanf("%d", &n);
          }
      while(n<3);
      u2=u1=1;        /*dwa pierwsze wyrazy*/
      i=2;
      while(i++<n)    /*uwaga, działa tylko dla n>2*/
                  {
                      u3=u1+u2;
                      u1=u2;
                      u2=u3;
                  }
                  /*inna możliwość*/
                  /*for(i=3; i<=n; i++, u1=u2, u2=u3) u3=u1+u2;*/
      printf("Wyraz o numerze %d ma wartosc %d", n, u3);
getchar();
getchar();
return 0;
}
```

---
Kod programu służącego do rysowania choinki (użycie pętli for):

```c
#include <stdio.h>
#define znak '*' /*znak wypełnienia*/
int main() {
    int lbwier; /*całkowita liczba wierszy*/
    int lw;     /*licznik wierszy*/
    int lodst;  /*liczba odstępów poprzedzających gwiazdkę*/
    int j;
    printf("ile wierszy?");
    scanf("%d",&lbwier);
    for(lw=0; lw<lbwier; lw++)
    {
              lodst=lbwier-lw-1;
              for(j=0; j<lodst; j++)
              putchar(' ');
              for(j=0; j<2*lw+1; j++)
              putchar(znak);
              putchar('\n');
    }
    getchar();
    getchar();
return 0;
}
```
Funkcja: 
```c
putchar(' ');
```
wyświetla pojedynczy znak.
<br>
*W apostrofach umieszczamy pojedynczy znak.

***
Kod programu służącego do wypisywania liczb całkowitych od 0 do 23

*pętla for:

```c
#include <stdio.h>
int main() {
int i;
for (i=0; i<=23; i++) {
printf("%d,", i);
}
getchar();
return 0;
}
```

*pętla while:

```c
#include <stdio.h>
int main() {
int i=0;
while (i<=23) {
printf("%d,", i);
i++;
}
getchar();
return 0;
}
```

*pętla do-while:

```c
#include <stdio.h>
int main() {
int i=0;
do {
printf("%d,", i);
i++;
}
while(i<=23);
getchar();
return 0;
}
```

Połączenie wszystkich 3 pętli w jednym programie -potrójnie wyświetla listę:

```c
#include <stdio.h>
int main() {
int i;
for (i=0; i<=23; i++) {
printf("%d,", i);
}
putchar('\n');


i=0;
while (i<=23) {
printf("%d,", i);
i++;
}
putchar('\n');


i=0;
do {
printf("%d,", i);
i++;
}
while(i<=23);

getchar();
return 0;
}
```

---

Kod programu wypisującego liczby od -3.5 do 7.5 z krokiem co 0.5 za pomocą 2 różnych pętli:

```c
#include <stdio.h>
int main() {
double i;
for (i=-3.5; i<=7.5; i=i+0.5) {
    printf("%.1lf,", i);
}

printf("\n\n\n");

i=-3.5;
while (i<=7.5) {
      printf("%4.1lf,\n", i);
      i=i+0.5;
}
getchar();
return 0;
}
```

---

Kod programu służącego do liczenia średniej z podanych liczb (użytkownik sam wybiera ilość liczb):

```c
# include <stdio.h>
int main () {
    int n, i;
    double x, suma=0.0, srednia;
    do     {
    printf("Podaj ilosc liczb (co najmniej 1):");
    scanf("%d", &n);
    }
    while(n<1);
    
    for(i=1;i<=n;i++) {
                     printf("Podaj %d liczbe:", i);
                     scanf("%lf", &x);
                     suma=suma+x;
                     }
    srednia=suma/n;
    printf("Suma podanych %d liczb wynosi: %lf \n", n, suma);
    printf("Srednia z podanych %d liczb wynosi: %lf", n,srednia);
    getchar();
    getchar();
    return 0;
}
```

---

Kod programu wyświetlającego kwadraty i sześciany liczb od 1 do podanej liczby przez użytkownika:

```c
#include <stdio.h>
int main() {
int i, n;
    printf("Podaj liczbe:");
    scanf("%d", &n);
    for(i=1;i<=n;i++) {    					/*Pętla for*/
	printf("%d %d %d \n", i, i*i, i*i*i);
    }
    
    printf("\n");								/*oddzielenie wyników*/
    
    i=1;										/*Pętla while*/
    while(i<=n)	{
	printf("%d %d %d \n", i, i*i, i*i*i);
	i++;
    }
    
    printf("\n");								/*oddzielenie wyników*/
    
    i=1;										/*Pętla do-while*/
    do	{
	printf("%d %d %d \n", i, i*i, i*i*i);
	i++;
		}
    while(i<=n);
    getchar();
    getchar();
    return 0;
}
```

---

Kod programu liczącego sumę kwadratów liczb naturalnych od 3 do 15:

```c
#include <stdio.h>
int main() {
int i, suma=0;
    for(i=3;i<=15;i++) {	/*Pętla for*/
		suma=suma+(i*i);
	}
	printf("%d \n",suma);
	
	printf("\n");		/*Rozdzielenie wyników */
	
	
	i=3;			/*Pętla while; w tym miejscu ustawiamy i */
	suma=0;			/*wyzerowanie sumy, ponieważ nie jest już =0*/
	while(i<=15)	{
	suma=suma+(i*i);
	i++;
	}
	printf("%d \n",suma);
    getchar();
    return 0;
}
```
---

Kod programu wypisującego wartości funkcji sin i cos dla kątów od 0 do 180 stopni ze skokiem 30 stopni:

```c
#include <stdio.h>
#include <math.h>
int main() {
double i;
    for(i=0;i<=180;i=i+30) {
       printf("sin(%.0lf)= %lf \n",i,sin(i*M_PI/180));
       printf("cos(%.0lf)= %lf \n\n",i ,cos(i*M_PI/180));
}
    getchar();
    return 0;
}
```
---
Kod programu, który wyświetla tabliczkę mnożenia do 13:

```c
#include <stdio.h> 
int main() 
{ 
int i,j; 
for(i=1;i<=13;i++) 	{ 
	for(j=1;j<=13;j++)	{
		printf("%4d ",j*i); 
						}
	putchar('\n'); 
					} 
getchar();
return 0;
}
```

---

Nieudana próba napisania kodu programu, który działa w pętli, aż użytkownik nie wciśnie "x"

```c
#include <stdio.h>
#define znak 'x'
int main() {
char i='a';
    while(i!=znak)    {
           puts("Podaj litere:");
           scanf("%c", &i);
           printf("Podales litere:%c \n",i);
        	}
           getchar();
           return 0;
}
```       

Jakiś pomysł jak go poprawić?

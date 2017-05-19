theme: Plain Jane
autoscale: true

# Java Class Structure

---

## Code style in the exam

- Don't expect best practices
- Really bad code there
- _The International Obfuscated C Code Contest:_ [http://www.ioccc.org/]()
    - http://www.ioccc.org/2015/dogon/prog.c

---

```C
#define So long
#define R rand()
#include <math.h>
#include <X11/Xlib.h>
#define T(i,F) ((So long)(i)<<F)
#define O(c,L,i) c*sin(i)+L*cos(i)
#define y(n,L) for(n=0; n<L 3; n++)     
#define P(v,L) d=0; y(l,)d+=T(L*l[v],l*20);
#define X(q) q>>10&63|q>>24&4032|q>>38&258048       
char J[1<<18]; int G[W*p],_,k,I=W/4+1,w=p/4+1; float C,B,e;            

unsigned So long A,n,d, t,h,x, f,o,r,a,l,L,F,i,s,H=1<<18,b=250,D[1<<14],z[W*p],q
=0x820008202625a0;main(){Display *j=XOpenDisplay(0);Window u=XCreateSimpleWindow
(j,RootWindow(j,0),0,0,W,p,1,0,0);XImage *Y=XCreateImage(j,DefaultVisual(j,0),24
,2,0,(char*)G,W,p,32,0); XEvent M; for(XMapWindow(j,u); XSelectInput( j,u,1)&&a-
65307; ){ if(!H){ if(XCheckWindowEvent(j,u,1,&M)){ a=XLookupKeysym(&M.xkey,0);*(
a&1?&C:&                                                                B)-=(.05
-a/2% 2*                                                                .1)*!(a-
1& 4092^                                                                3920);a+
2&0xfe0^                                                                0xfc0||(
s=a+2&31                                                                ); }else
{ y(k,p+        ){ F=k%w* 4|k/w;               float a[6],S=(F-p        /2.) /p;
y(_,W+){        i=_%I*4|_/I; if(               F<p&i<W){ o=1; L=        i+F*W;if
(l=i&3);        else{ l=F&3; o=W               ; } h=z[L-o*l]; f        =z[L+(4-
l)*o]; t        =F-p/2||i-W/2; r               =h^f; if(!l| !t|(        int)r|(!
(h- 3&3)        &&258063&r>>38))               { float V=(i-W/2.        )/p,U=O(
S,1,B),m        =32768,Q=m; a[4]               =O(-1,S,B); a[3]=        O(U,V,C)
; a[5]=O        (-V,U,C); P((a+3               ),s*42); t||(A=d)        ;f=0;y(n
,){float        N=a[n+3], E=1024               /fabs(N); b= N<0;        float K=
(((q>>20        *n)^~-b)+!b&1023               )/1024.; y(d,)a[d        ]=a[d+3]
*E; a[n]        =round(a[n]); P(               a,K); i=q+d; P(a,        1); e=E*
K; for(;                e<m; i+=d){ l=X(i); t=r=l^(l^l-(                1<<6*n))
&63<<6*n                ; if(b){ r=l; l=t; } if(J[r])l=r                ; if(t=J
[l]){x=(                n-1)?(i|i>>40)&1023|i>>8&4190208                |4194304
:i&1023|                i>>28&4190208|(b^l==r)<<23; if(h                =D[(x>>6
&0xf|x>>                14&0x3f0)+t*768]){ o=h; f=n|l*4|                x<<32; m
=e; } if                (t==8&e<Q)Q=e; } e+=E; } }b=(255                -((f&3)+
2)%3*51)                *(1-m/32768); o=o*b>>8; G[L]=o>>                32<<8|o&
16711935                ; z[L]=3*(Q<=m)|f|b<<56; } else{                d=l*(f<<
8>>40)+(                4-l)*(h<<8>>40)>>2&16774143; o=D                [(d>> 6&
15|d>>14                &1008)+J[(int)h/4]*768]*(b=h>>56                )>>8; G[
L]=o>>32                <<8 | o&                16711935                ; z[L]=(
int) h|d                <<32|b<<                56; } }}                } q +=A;
XPutImage               (j, u+0,               DefaultGC                (j,J[X(q
)]=0),Y,                0,0,0,0,                W,p); }}                else{ L=
--H/768;                J[H] =R%                16*(R%4<                abs((H>>
6&63)-32                                                                )+abs((H
>>12&63)                                                                -32)-3); 
i=H &15;                                                                F=H %768
>>4; if(                                                                L<16){if
(L-1|!(R                                                                %3))b=R%
96^255; l=i*i*3+i*81/4&3; a=L>3?L-8?L-5?9858122:12365733-488848*((i+F/4*4)%8&&F%
4):R%2*5298487:3352537*L*L-14202379*L+19205553; if(L==4)if(F<l+18)a=6990400;else
if(l>F-19)b*=0.7; if(L==3){ if((i-1&15)<14&(F-1&15)<14&!(F&16)){ a=12359778; _=7
-i; k=7-F%16; _^=_>>31; k^=k>>31; b=196-R%32+(k>_?k:_)%3*42;} else{ b*=1+R%2*(.5
-(i&1)); } } D[H]=(a&16711935|(a&65280)<<24)*(b>>(F>>5))>>8&0xff00ff00ff; } } }}


```

---

## Classes vs. Objects

- Class: building blocks. Template to create objects
- Objects: runtime instances of classes
- State: all objects of all our classes


---

## Class members

- Fields: class-level variables
- Methods: _functions_, _procedures_
- Method signature: 

`access modifier` `return type` methodName(`parameter type` `parameter name`, ...) 

---

## Valid class

```java
public class Person {
	
}

...

class House {
	Person owner;
	int rooms;
	void cleanRoom(int roomNumber) {}
}

```

---

## Java building blocks

- __Classes__
- __Interfaces__
- Enums (OCP)

---

## 😱 Spot errors

```java
public class Main {
    public static void main(String[] args) {
        new House().rooms();
    }
}

class House {
    String ownerName;
    int rooms;
    void cleanRoom(int roomNumber) {
        roomNumber = rooms;
    }
    int Rooms;
    int rooms() {}
}
```

---

## 😱 Missing return statement

### Easier with an IDE & compiler, right? :-D

---

## Comments

```java
// one line Comments

/*
Multiline comment
*/

/*
 * Fancy Multiline comment
 *
 */
 
/**
 *
 * Java Doc comment (NOT IN THE EXAM)
 */
```

---

## 😱 Spot errors

```java
// hello // world

/* // hello world */

/*
/*
// Hello
// World
 */
 */

```

---


## Rules .java source files

- one public class in every file, at most
- if there's one public class -> file name same as class
- as much non-public classes as we want

---

## 😱 Spot errors

```java
// Wolf.java

class Wolf {
}

class wolf {
    
}

```

---
## 😱 Spot errors

```java
// House.java

public class House {
}

class Person {

}

class Monkey {

}
```

---

## Main method

- Entry point to our program
- Java Runtime injects parameters

```java
public static void main(String[] args) {

}
```

---

## Main method II
### All valid

```java
public static void main(String[] main) {
	// write your code here
}

public static void main(String... main) {
	// write your code here
}

public static void main(String m[]) {
	// write your code here
}
```

---

## 😈 Watch out

```java
public void main(String m[]) {
	// write your code here
        System.out.println("Hello");
}
```

```bash
Error: el método principal no es static en la clase Main, 
defina el método principal del siguiente modo:
   public static void main(String[] args)

```
---

## 😱 Spot errors

```java
public class Main {
    public static void main(String args) {
        new House().rooms();
    }
}

class House {
    String ownerName;
    int rooms;
    void cleanRoom(int roomNumber) {
        roomNumber = rooms;
    }
    int Rooms;
    int rooms() { return rooms; }
}
```

---

## 😱 Spot errors

```java
public class Main {
    public static void main(String args) { // array of Strings!
        new House().rooms();
    }
}

class House {
    String ownerName;
    int rooms;
    void cleanRoom(int roomNumber) {
        roomNumber = rooms;
    }
    int Rooms;
    int rooms() { return rooms; }
}
```

---

## Exercise: print all parameters from command line

- if its a number?


---

## JRE vs JDK

- JRE: to __run__ Java programs
- JDK: to __compile__ Java programs
- JDK contains a JRE in order to run (test) programs
    - inside the JDK folder there's a JRE with `java` command
    - `javac` & other tools, only in JDK

---

## Compiling from command line

```bash
$ javac -version
$ java Main
```

- Compile & run classes by hand. Read page 14

---

## Imports

- PIC: Package, Imports, Classes
- `import java.lang.*;` by default
- import one class or all classes in that package (wildcard)
- __non recursive__
- package name: lowercase legal identifiers separated by .

---

## 😈 Watch out

Redundant

```java
import java.lang.Exception;
import java.lang.*;
```

Error

import java.lang.*.*;

---

## Packages as namespaces

- avoid conflicts with two classes, same name
- FQCN: Fully Qualified Class Name
- default package == no package


---
## 😈 Watch out

Error!

```java

import java.sql.Date;	// try with *
import java.util.Date;

public class Main {
    public static void main(String m[]) {
        Date d;
    }
}
```

---

## Exercise

- create our own packages, compile from command line
- launch from command line `java package.ClassWithMainMethod`

---

## Constructors

- methods to initialize objects __after__ creation
- creation in three phases
- Stack (references), Heap (Objects, References)

---

## 😈 Watch out

```java

public class A {
    String a = "Wow";
    
    public A() {
        a = "much A's";
    }
    
    public void A() {
        
    }

    public static void main(String m[]) {
        A a = new A();
    }
}
```

---

## Using object fields (get & set values)


```java

public class A {
    String a = "Wow";
    String s = a + " much String!";    // reading field

    public static void main(String m[]) {
        A a = new A();
        
        a.a = "Hello";                  // setting field

        System.out.println(a.a);        // reading field
    }
}

```


---

## Instance initializer blocks

```java

public class Doge {
    String meme = "Wow!";

    {
        meme += "Much instance initializer blocks ";
    }

    public Doge() {
        meme += " so exciting";
    }

    public static void main(String[] args) {
        Doge d = new Doge();

        System.out.println(d.meme);
    }

    {
        meme += " very confusing!";

    }
}

```

---

## Instance initializer blocks

## [fit] WAT

---

![](img/mickey.gif)

---

## Instance initializer blocks

- only for people who doesn't know to __chain__ constructors
- to make code confusing
- to build objects _without_ using constructors


---


## Java Reserved words


```java
abstract	boolean	     break	    byte	     case	    catch
char	    class	     const	    continue	 default	do
double	    else	     extends	final	     finally	float
for	        goto	     if	        implements	 import	    instanceof
int	        interface    long	    native	     new	    package
private	    protected    public	    return	     short	    static
strictfp	super	     switch	    synchronized this	    throw
throws	    transient	 try	    void	     volatile	while
assert	    enum				
```

---

## Misterios

- Transient: no se serializa esa propiedad (y así no se graba a disco / envia por la red)
- Volatile: puede ser accedida por múltiples hilos: está sincronizada
- Strictfp: compatibilidad operaciones floating point [^1]
- Goto: reservado [^2]


[^2]: http://www.youtube.com/watch?v=9ei-rbULWoA&t=17m25s

[^1]: https://www.securecoding.cert.org/confluence/display/java/NUM06-J.+Use+the+strictfp+modifier+for+floating-point+calculation+consistency+across+platforms

---

## Tipos primitivos vs. Clases Wrapper

boolean	Boolean	
byte	Byte	
char	Character	
double	Double
float	Float
int	    Integer
long	Long
short	Short

---

## Identificadores

- Legales: los que compilan
- Convenciones de código de Sun
- Estándares de nombrado de JavaBeans

---


## Convenciones de nombres Sun

- Clases: 1ª mayúscula + CamelCase
- Interfaces: 1ª mayúscula + CamelCase
- atributos: 1ª minúscula + CamelCase
- métodos: 1ª minúscula + CamelCase
- constantes: CONST_NAME


---

## JavaBeans naming standars

- JavaBean:
    - constructor público sin argumentos
    - propiedades privadas
    - get / set / is (boolean)
    - public void setProp(PropTipo val)
    - public PropTipo getProp();
    - Listeners:
        - add / remove Listener


---


## Identificadores: reglas

- empiezan por letra [A-Za-z], $, _
- NO empiezan por número
- desp. del 1er. carácter, cualquier combinac de letras, números y $,_
- case sensitive
- no se pueden usar las palabras clave de Java

---

## Identificadores (test)

```java

int $$;	
int $___10;	
int 1niesta;	
int :hola;	
int hola:;	
int otro_identificador$;	
int e$te_e$ta_mal;	
int pero-Este-Bien;	

```

---

## Reference types

- reference: pointer
- references: variables en la pila, apuntan a objetos en el heap
- Stack:
    - variables locales
    - parámetros
- Heap:
    - variables de instancia (iVars)
    - objetos

```java

String name = null;

```

---

## Declarando variables

- declarar variables tipos simples
    - no podemos usar `null` con tipos simples
- declarar variables referencias

---

## Declarando variables

```java

int i = null;

String s1, s2, s3;

s1 = new String("Hello");
s2 = "World!";


```


---

```java
MiClase c = new MiClase();
```

- instancia un nuevo objeto en el montón
- lo inicializa
- lo liga a la referencia c (que es una var. local, luego está en la pila)

---

## Variable initialization (rules)

- local vars
- fields
    - iVars: se establecen a un valor por defecto
    - primitivos
    - referencias a objetos
    - arrays
- class variables

---

## Blocks of code & variable scope

- class
- method
- if, while, switch, ...

```java

int i = 10;

{
    int i = 11;     // error: redefining var
    int j = 10;     // only visible inside block
}

```

---
## alcance de variables

- static
- iVars
- local / automatic
- block

---

## Order of elements

- PIC: Package, Imports, Classes
- methods, fields: everywhere


---

## Destroying objects

- Garbage collector
- `finalize()`
    - not guaranteed to be called
- `jconsole`

---

## Benefits of Java

- OO
- Encapsulation
- Platform independent
- Robust
- Simple
- Secure

---

## Examples of Encapsulation & Coupling
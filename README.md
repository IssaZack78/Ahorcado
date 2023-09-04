# EJERCICIO A: TRIPLE DE PITAGORAS
![image](https://github.com/IssaZack78/Ahorcado/assets/143243575/b4102a16-3a2d-47f9-b382-3881ad15ea76)

INSTRUCCIONES:
* Encuentre todos los triples de Pitágoras para lado1, lado2, y la hipotenusa, que no sean mayores de 500.
---
# TRIPLE DE PITAGORAS EN PYTHON
```PYTHON
#Triple Pitágoras 
import math
a = float(input("Ingresar el Primer cateto como: "))
b = float(input("Ingresar el Segundo cateto como: "))
h = math.sqrt(a*a+b*b)
print("El valor de la hipotenusa es:",h)
```
# TRIPLE DE PITAGORAS EN C++
```C++
/*Algoritmo que mueste Triple de Pitágoras*/
#include <iostream>
using namespace std;

int main()  {
    float a, b, h =0;
    cout << "\t\t\tTriple Pitágoras" <<
    cout << "\nIngrese el Primer Cateto como a: ";
    cin >> a;
    cout << "\nIngrese el Primer Cateto como b: ";
    cin >> b;
    h=pow(a,2) + pow(b,2);
    h=math.sqrt(h);
    cout << "\n\nEspere un Segundo...";

    cout << "\t\t\tResultado";
    cout << "\n\nLa hipotenusa es: "<< h;
    cout << endl;
    return 0;
}
```

# TRIPLE DE PITAGORAS EN PSEINT(PSEUDOCODIGO)
```PSEINT
Algoritmo Tripe_de_Pitágoras
	Definir a, b, h Como Real
	a<-Aleatorio(0,500)
	b<-Aleatorio(0,500)
	Escribir "Ingrese el primer valor como Cateto a: "
	leer a
	Escribir "Ingrese el segundo valor como cateto b: "
	leer b
	Si a<=500 Entonces
	Fin Si	
		Si b<=500 Entonces
			h <- (raiz(a^2 + b^2));
	SiNo
		Escribir "la opción es inválida"
		Fin Si	
	Escribir "la hipotenusa es: ",h;
FinAlgoritmo
```

# EJERCICIO B: AHORCADO
![image](https://github.com/IssaZack78/Ahorcado/assets/143243575/cb30a083-c97b-499e-b314-c9769c83ea5f)

INSTRUCCIONES: 
* Ingrese una palabra.
* La siguiente persona tendra que adivinar la palabra secreta letra por letra.
* Si la persona adivina la palabra secreta, Gana, de lo contrario sera AHORCADO.
---
# JUEGO DEL AHORCADO EN PYTHON
```PYTHON
import random

def obtener_palabra_aleatoria():
    palabras=["murcielago", "arbol", "avion", "llave", "navidad", "nieve"] 
    palabra_aleatoria=random.choice(palabras)
    return palabra_aleatoria

def mostrar_codigo(palabra_secreta, letras_adivinadas):
    codigo=""
    for letra in palabra_secreta:
        if letra in letras_adivinadas:
            codigo+=letra
        else:
            codigo+="-"
        print(codigo)

def jugar_ahorcado():
    palabra_secreta=obtener_palabra_aleatoria()
    letras_adivinadas=[]
    intentos_restantes=5

    while intentos_restantes>0:
        mostrar_codigo(palabra_secreta, letras_adivinadas)
        letra=input("Ingresa la letra: ").lower()

        if letra in letras_adivinadas:
            print("error, intenta otra letra.")
            continue

        if letra in palabra_secreta:
            letras_adivinadas.append(letra)
            if set(letras_adivinadas)==set(palabra_secreta):
                print("Felicidades!!! Has Ganado!!!")
                break
        else: 
            intentos_restantes==1
            print(f"letra incorrecta. Te quedan {intentos_restantes}")
    if intentos_restantes==0:
        print(f"Estas Ahorcado. La Palabra Secreta Es: {palabra_secreta}")  

jugar_ahorcado()
```
# JUEGO DEL AHORCADO EN C++
```C++
# include <iostream>
# include <string>

string palabra_original;
string palabra_secreta;
int vidas;

void secreta();
void ingresar(char x);
void inicializar();

int main(){
    inicializar();
    secreta();
    while (vidas>0 && palabra_secreta!=palabra_original ){
        char x;
        cin>>x;
        system("clear"); //system("cls");
        ingresar(x);
        secreta();
    }
    if(vidas>0) cout<<"¡¡Ganaste!!"<<endl;
    else cout<<"Perdiste, Estas Ahorcado. La palabra correcta es: "<<palabra_original<<endl;
}

void secreta(){
    cout<<"vidas: "<<vidas<<endl;
    cout<<palabra_secreta<<endl;
}

void inicializar(){
    int vidas = 5;
    string palabra_original="Ahorcado";

    for(int i=0 ; i<palabra_original.length() ; i++){
        if(palabra_original[i]>='A' && palabra_original<='Z'){
            palabra_original[i]+=32;
        }
    }

    for(int i=0 ; i<palabra_original.length() ; i++){
        if(palabra_original[i]>='a' && palabra_original[i]<='z'){
            palabra_secreta+='_';
        }else{
            palabra_secreta+=palabra_original[i];
        }
    }

    mostrar();
}

void ingresar(char x){
    bool perdividas=true;

    for(int i=0 ; i<palabra_original.length() ; i++){
        if(x==palabra_original[i]){
            perdividas=false
            palabra_secreta[i]=x;
        }
    }

    if(perdividas) vidas--;        
}
```
# JUEGO DEL AHORCADO EN PSEINT(PSEUDOCODIGO)
```PSEINT
Algoritmo JUEGO_DE_AHORCADO
	Definir letra, secreto, Vector1, Vector2 como caracter
	Definir a, n, i, error Como Entero
	Escribir "Ingrese una palabra oculta"
	leer secreto
	n<-Longitud(secreto)
	Dimension Vector1(n), Vector2(n)
	Para i<-1 Hasta n Con Paso 1 Hacer
		Vector1(i) <- Subcadena(secreto,i,i)
		Vector2(i) <- "_"
	Fin Para
	a<-0
	Mientras a<5 Hacer
		Para i<-1 Hasta n Con Paso 1 Hacer
			Escribir Vector2(i) Sin Saltar
		Fin Para
		Escribir " "
		Escribir "Ingrese una letra"
		leer letra
		error <- 1
		para i <- 1 Hasta n Con Paso 1 Hacer
			si letra == Vector1(i) Entonces
				si Vector2(i) == "_" Entonces
					Vector2(i) <- letra
					j <- j + 1
					error <- 0
				FinSi
			FinSi
		FinPara
		si j == n Entonces
			Escribir "Has Ganado!!!, Felicidades!!!"
			a <- 6
		SiNo
			si error == 1 Entonces
				a <- a + 1
			FinSi
			Si a == 1 Entonces
				Escribir "......"
				Escribir ".....o"
				Escribir "."
				Escribir "."
				Escribir "Te quedan 4 intentos"
			FinSi
			si a == 2 Entonces
				Escribir "......"
				Escribir ".....o"
				Escribir ".....|"
				Escribir "."
				Escribir "Te quedan 3 intentos"
			FinSi
			si a == 3 Entonces
				Escribir "......"
				Escribir ".....o"
				Escribir ".....^"
				Escribir ".....|"
				Escribir "Te quedan 2 intentos"
			FinSi	
			si a == 4 Entonces
				Escribir "......"
				Escribir ".....o"
				Escribir ".....^"
				Escribir ".....|"
				Escribir ".....^"
				Escribir "Te quedan 1 intento"
			FinSi	
			si a == 5 Entonces
				Escribir "......"
				Escribir ".....o"
				Escribir "...--- "
				Escribir ".....^"
				Escribir ".....|"
				Escribir ".....^"
				Escribir "Estas Ahorcado"
			FinSi	
		FinSi
	Fin Mientras
FinAlgoritmo
```

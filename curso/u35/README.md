# Funciones y procedimientos

Partimos del ejemplo anterior de función:

	#include <iostream>
	using namespace std;

	int CalcularMaximo(int num1,int num2);

	int main(int argc, char *argv[]) {
		int numero1,numero2,num_maximo;
		cout << "Dime el número1:";
		cin >> numero1;
		cout << "Dime el número2:";
		cin >> numero2;
		num_maximo = CalcularMaximo(numero1,numero2);
		cout << "El máximo es " << num_maximo;
		return 0;
	}

	int CalcularMaximo(int num1,int num2)
	{
		if(num1>num2)
			return num1;
		else
			return num2;
	}

## Devolución de resultados

Cuando la función finaliza hemos dicho que se devuelve un valor (Recuerda que los procedimientos no devuelven valor). Para devolver un valor usamos la instrucción `return` seguida del valor a devolver. Una función puede tener varias instrucciones `return`, cuando se ejecuta una se devuelve el valor y se termina la ejecución de la función.

## Llamada a la función

Para llamar a una función se debe utilizar su nombre y entre paréntesis los parámetros reales que se mandan. La llamada a una función se puede considerar una expresión cuyo valor y tipo es el retornado por la función. Evidentemente si estamos llamando un procedimiento, la llamada no tendrá ningún tipo.

Ejemplos de llamadas:

	num1 = CalcularMaximo(5,6);
	cout << CalcularMaximo(1,2);
	...

## Ámbito de variables

Las variables definidas en la función no existen en otras funciones o el programa principal. Igualmente las variables del programa principal no existen en la función.

Por ejemplo la variable max definida en la función no existe en el programa principalmente. Igualmente la variable numero1 definida en el programa principal no existe en la función.
Parámetros formales y reales

* **Parámetros formales**: Son las variables que recibe la función, se crean al definir la función. Su contenido lo recibe al realizar la llamada a la función de los parámetro reales. Los parámetros formales son variables locales dentro de la función.

* **Parámetros reales**: Son la expresiones que se utilizan en la llamada de la función, sus valores se copiarán en los parámetros formales.

## Paso de parámetro por valor o por referencia

* **Paso por valor**: El valor de los parámetros reales se copian en los parámetros formales, por lo tanto una modificación de algún parámetro formal no modifica el parámetro real.
* **Paso por referencia**: Cuando se pasa un parámetro por referencia implica que si modificamos el parámetro formal se modificará el parámetro real. Para poder modificar los parámetros reales vamos a usar **punteros**, de esta manera mandaremos a la función un puntero (parámetro formal) al parámetro real y de esta manera la podremos modificar.


## Ejemplos

Comprobamos que los parámetros pasados por valor no modifican los parámetros reales.

	#include <iostream>
	using namespace std;
	void PasoPorValor(int num);

	int main(int argc, char *argv[]) {
		int numero1=5;
		PasoPorValor(numero1);
		cout << numero1 << endl;
		return 0;
	}

	void PasoPorValor(int num)
	{
		num = num + 1;
		cout << num << endl;
	}

El resultado será 6 y 5. Hemos incrementado el valor del parámetro formal, pero no se ha modificado el real.

Veamos ahora el mismo programa pero pasando el parámetro por referencia.

	#include <iostream>
	using namespace std;
	void PasoPorReferencia(int *num);

	int main(int argc, char *argv[]) {
		int numero1=5;
		PasoPorReferencia(&numero1);
		cout << numero1 << endl;
		return 0;
	}

	void PasoPorReferencia(int *num)
	{
		*num = *num + 1;
		cout << *num << endl;
	}


El resultado será 6 y 6. Hemos modificado el parámetro formal y se modificado el real.


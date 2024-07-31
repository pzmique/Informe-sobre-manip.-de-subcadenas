## Luca_Bagnato Nicolas_Ortino Miqueas_Paz
# Informe sobre manipulación de Cadenas en C++ 
## Objetivo

El objetivo de este informe es que los alumnos demuestren su comprensión sobre la
manipulación de cadenas en C++ utilizando tanto arreglos de caracteres (`char[]`) como
la clase ``std::string`` de la biblioteca estándar. Deben incluir ejemplos de código,
explicaciones y comentarios sobre las diferencias y ventajas de cada enfoque.


## Instrucciones
El informe debe estar escrito en formato Markdown y debe incluir las siguientes
secciones:

## 1. Introducción
   
* Breve introducción sobre qué son las cadenas de caracteres en C++.
* Diferencias básicas entre `char`, y `std::string` 


En C++, una cadena de caracteres es una secuencia de caracteres que se utilizan para representar texto. Hay dos formas principales de trabajar con cadenas de caracteres en C++:

### 1.  Cadenas de caracteres en estilo C (C-strings): 
   - Se representan como un arreglo de caracteres (`char[]`), que termina con un carácter nulo (`'\0'`). 
   ```cpp
     Ejemplo: char saludo[] = "Hola, mundo!";
   ```
   - Estas cadenas son gestionadas manualmente y carecen de algunas funcionalidades que tienen otras clases.

### 2.  Cadenas de caracteres en estilo C++ (std::string):
   - Se representan mediante la clase std::string de la biblioteca estándar C++. 
   ```cpp
   - Ejemplo: std::string saludo = "Hola, mundo!";
   ```
   - Ofrecen una interfaz más sencilla y poderosa para manipular texto, incluyendo operaciones como concatenación, comparación, y búsqueda.





## 2. Declaración e Inicialización de Cadenas

* Ejemplo de cómo declarar e inicializar una cadena usando `char[]`.
```cpp
#include <iostream>

int main() {
    // Declarar e inicializar una cadena de caracteres
    char saludo[] = "Hola, mundo!";
    
    // Imprimir la cadena
    std::cout << saludo << std::endl;
    
    return 0;
}

```
* Ejemplo de cómo declarar e inicializar una cadena usando ``std::string``.
```cpp
#include <iostream>
#include <string> // Incluir la cabecera para std::string

int main() {
    // Declarar e inicializar una cadena de caracteres usando std::string
    std::string saludo = "Hola, mundo!";
    
    // Imprimir la cadena
    std::cout << saludo << std::endl;
    
    return 0;
}

```
### Explicación de los ejemplos.
#### Ejemplo 1
* char saludo[] = "Hola, mundo!"; crea un arreglo de caracteres que contiene la cadena "Hola, mundo!" y automáticamente agrega el carácter nulo al final.

#### Ejemplo 2 
* std::string saludo = "Hola, mundo!"; crea un objeto de tipo std::string que contiene la cadena "Hola, mundo!".


## 3. Concatenación de Cadenas
* Ejemplo de concatenación usando `char[]` y la función `strcat`.

```cpp
#include <iostream>
#include <cstring> // Necesaria para std::strcat

int main() {
    // Declarar e inicializar las cadenas
    char saludo[50] = "Hola, "; // Tamaño suficiente para la concatenación
    char nombre[] = "mundo!";
    
    // Concatenar las cadenas
    std::strcat(saludo, nombre);
    
    // Imprimir la cadena resultante
    std::cout << saludo << std::endl;
    
    return 0;
}

```
* Ejemplo de concatenación usando ``std::string`` y el operador `+`.
```cpp
#include <iostream>
#include <string> // Necesaria para std::string

int main() {
    // Declarar e inicializar las cadenas
    std::string saludo = "Hola, ";
    std::string nombre = "mundo!";
    
    // Concatenar las cadenas
    std::string resultado = saludo + nombre;
    
    // Imprimir la cadena resultante
    std::cout << resultado << std::endl;
    
    return 0;
}

```
* Explicación de los ejemplos y comentarios sobre la facilidad de uso y eficiencia.

### Explicación del ejemplo 1:

* char saludo[50] = "Hola, "; declara un arreglo de caracteres con suficiente espacio para almacenar el resultado concatenado.

* std::strcat(saludo, nombre); concatena la cadena nombre al final de saludo. La función strcat requiere que el arreglo de destino (saludo) tenga suficiente espacio para almacenar la cadena concatenada más el carácter nulo final.

* Facilidad de uso: Es menos intuitiva y más propensa a errores si el tamaño del arreglo no se maneja adecuadamente.

* Eficiencia: strcat puede ser menos eficiente en ciertos casos debido a la necesidad de recorrer la cadena de destino para encontrar el final, además de que la gestión del tamaño del arreglo debe ser manual.

### Explicacion del ejemplo 2:

* std::string saludo = "Hola, "; y std::string nombre = "mundo!"; crean objetos std::string que contienen las cadenas deseadas.

* std::string resultado = saludo + nombre; utiliza el operador + para concatenar las dos cadenas de manera sencilla y directa.

* Facilidad de uso: Mucho más intuitiva y segura. La clase std::string maneja automáticamente el tamaño y la memoria, reduciendo el riesgo de errores.

* Eficiencia: Generalmente, std::string puede ser más eficiente y ofrece una mejor gestión de memoria, ya que maneja internamente las operaciones de concatenación y ajuste de tamaño.


## 4. Longitud de una Cadena
* Ejemplo de cómo obtener la longitud de una cadena usando `char[]` y la función `strlen`.

```cpp 
#include <iostream>
#include <cstring> // Necesaria para std::strlen

int main() {
    // Declarar e inicializar la cadena
    char saludo[] = "Hola, mundo!";
    
    // Obtener la longitud de la cadena
    size_t longitud = std::strlen(saludo);
    
    // Imprimir la longitud
    std::cout << "La longitud de la cadena es: " << longitud << std::endl;
    
    return 0;
}

```
* Ejemplo de cómo obtener la longitud de una cadena usando ``std::string`` y el método `length`.
```cpp
#include <iostream>
#include <string> // Necesaria para std::string

int main() {
    // Declarar e inicializar la cadena
    std::string saludo = "Hola, mundo!";
    
    // Obtener la longitud de la cadena
    std::size_t longitud = saludo.length();
    
    // Imprimir la longitud
    std::cout << "La longitud de la cadena es: " << longitud << std::endl;
    
    return 0;
}

```
* Explicación de los ejemplos.

### Explicacion  del ejemplo 1:

* char saludo[] = "Hola, mundo!"; crea una cadena de caracteres en estilo C.

* std::strlen(saludo); calcula la longitud de la cadena, excluyendo el carácter nulo de terminación ('\0'). La función strlen devuelve un valor de tipo size_t, que es el tamaño de la cadena.

* Notas: strlen recorre la cadena hasta encontrar el carácter nulo, por lo que la eficiencia puede verse afectada por la longitud de la cadena. Además, la cadena debe estar bien formada con el carácter nulo al final para evitar errores.

### Explicacion del ejemplo 2:

* std::string saludo = "Hola, mundo!"; crea un objeto std::string.

* saludo.length(); devuelve la longitud de la cadena, incluyendo todos los caracteres y excluyendo el carácter nulo (internamente, std::string maneja la longitud y el carácter nulo automáticamente). El método length devuelve un valor de tipo std::size_t, que es el tipo adecuado para representar tamaños.

* Notas: El método length de std::string es generalmente más eficiente y fácil de usar, ya que la clase std::string maneja internamente la longitud y otros detalles de la cadena.

## 5.Subcadenas
* Ejemplo de cómo obtener una subcadena usando ``std::string`` y el método `substr`.

```cpp
#include <iostream>
#include <string>

int main() {
    // Crear una cadena de caracteres
    std::string texto = "Hola, mundo!";
    
    // Obtener una subcadena usando el método substr
    // sintaxis: substr(posicion, longitud)
    std::string subcadena = texto.substr(0, 4);  // Desde el índice 0, tomar 4 caracteres

    // Mostrar la subcadena
    std::cout << "La subcadena es: " << subcadena << std::endl;

    return 0;
}

```
* Explicación del ejemplo.

```cpp
#include <iostream>
#include <string>

```
* #include <iostream> permite usar std::cout para la salida de datos.

* #include <string> incluye la definición de la clase std::string.

```cpp
std::string texto = "Hola, mundo!";
```

* Se crea una variable texto de tipo std::string e inicializa con el valor "Hola, mundo!".

```cpp
std::string subcadena = texto.substr(0, 4);
```

* texto.substr(0, 4) obtiene una subcadena de texto.

* El primer argumento 0 indica la posición de inicio (índice 0 en este caso).

* El segundo argumento 4 es la longitud de la subcadena que queremos extraer.

```cpp
std::cout << "La subcadena es: " << subcadena << std::endl;
```

* Imprime en la consola la subcadena obtenida.

## 6. Comparación de Cadenas
* Ejemplo de comparación usando `char[]` y la función `strcmp`.

* Ejemplo de comparación usando ``std::string`` y operadores relacionales.
* Explicación de los ejemplos y comentarios sobre la facilidad de uso y seguridad.

## 7. Otras  Operaciones Útiles
* Ejemplo de cómo convertir una cadena a mayúsculas o minúsculas usando `std::string` y las funciones `toupper` y `tolower`.
* Ejemplo de cómo buscar caracteres o subcadenas en una `std::string` usando el método `find`.
* Conversión de cadenas a números
* Pasaje de Cadenas a Funciones en C++
  - Pasaje de Cadenas Usando `char[]`
  - Pasaje de Cadenas Usando `std::string`
* Explicación de los ejemplos.

## 8. Conclusión
* Resumen de las principales diferencias entre `char[]` y `std::string`.
* Ventajas y desventajas de usar cada uno.
* Recomendaciones personales sobre cuándo usar cada enfoque.

## 9. Referencias
* Cualquier referencia utilizada para crear el informe.
* Criterios de Evaluación
* Estructura y Organización
* Contenido y Comprensión
* Explicaciones y Comentarios
* Formato y Estilo  
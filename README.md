# Práctica 11. Ficheros.

# Factor de ponderación: 9

### Objetivos
Los objetivos de esta práctica son que el alumnado:
- Sea capaz de resolver problemas sencillos en C++ usando todos los conocimientos adquiridos hasta ahora, y en particular utilizando funciones y ficheros de texto
- Diseñe, desarrolle y utilice funciones en sus programas haciendo que sus programas sean modulares

### Rúbrica de evaluacion de esta práctica
Se señalan a continuación los aspectos más relevantes (la lista no es exhaustiva) que se tendrán en cuenta a la hora de evaluar esta práctica. Se comprobará que el alumnado:
- Conoce los conceptos expuestos en el material de referencia de esta práctica
- Ha realizado todos los ejercicios propuestos en este enunciado
- Es capaz de escribir programas simples en C++ que resuelvan problemas de complejidad similar a los que se proponen en este documento
- Hace que sus programas se estructuren en torno a diferentes funciones (sean modulares)
- Todos sus programas se estructuran en directorios diferentes, cada uno con un fichero `Makefile` que automatice su compilación
- Utiliza en todos sus programas comentarios adecuados en el formato requerido por [Doxygen](https://www.doxygen.nl/index.html)
- Acredita que es capaz de subir programas a la plataforma [Jutge](https://jutge.org/) para su evaluación
- Ha incluido un comentario prólogo en todos los ficheros (`*.cc`, `*.h`) de sus ejercicios
- Que todos los programas que desarrolla imprimen en pantalla un mensaje indicando la finalidad del programa, así como la información que precisará del usuario para su correcta ejecución
- Hace que todos los programas que se presentan para su evaluación cumplan con los estándares definidos en la [Guía de estilo de Google para C++](https://google.github.io/styleguide/cppguide.html)
- Utiliza siempre identificadores significativos en su programa (para constantes, variables, etc.) y no utiliza nunca identificadores de una única letra, excepto tal vez para las variables que utilice para iterar en un bucle
- Acredita que es capaz de editar ficheros remotos en su VM usando Vi
- Ha realizado todos sus ejercicios en la máquina virtual Ubuntu de la asignatura.
- Demuestra que es capaz de ejecutar comandos Linux en su VM

### Material de estudio complementario
Estudie del [tutorial de referencia](https://www.learncpp.com/) en la asignatura los siguientes apartados:
- [28.1 Input and output (I/O) streams](https://www.learncpp.com/cpp-tutorial/input-and-output-io-streams/)
- [28.2 Input with istream](https://www.learncpp.com/cpp-tutorial/input-with-istream/)
- [28.3 Output with ostream and ios](https://www.learncpp.com/cpp-tutorial/output-with-ostream-and-ios/)
- [28.6 Basic file I/O](https://www.learncpp.com/cpp-tutorial/basic-file-io/)

### Ejercicios
- Al realizar los ejercicios cree dentro de su repositorio de esta práctica un directorio diferente para cada uno de los ejercicios. Asigne a cada uno de esos directorios nombres significativos.
- Automatice la compilación del programa correspondiente a cada ejercicio con un fichero `Makefile` independiente para cada programa e inclúyalo en el correspondiente directorio
- Haga que todos los programas tomen su entrada por la línea de comandos y en caso de que se ejecuten sin pasarles el número adecuado de parámetros impriman en pantalla un mensaje indicando el modo correcto de ejecutar el programa.
- El código de cada uno de los programas deberá organizarse de forma modular, es decir haciendo uso de funciones
- Cada función deberá realizar una única tarea y hacerlo correctamente
- El identificador de una función debe reflejar claramente la finalidad de la función

Para realizar pruebas con los siguientes ejercicios, puede utilizar el documento *Quijote.txt* enlazado en el apartado de la práctica 3 del Aula Virtual de *Informática Básica.*

1. Escriba un programa que imprima en pantalla la palabra con mayor número de vocales y la palabra con el mayor número de consonantes (independientemente de si se trata de mayúsculas o minúsculas) que se encuentren en un fichero de texto que se le pase como parámetro por línea de comandos. En caso de empate (haya varias palabras con igual número de vocales/consonantes) el programa imprimirá la palabra que aparezca antes en el fichero de texto.

2. Escriba un programa que *rote* las vocales en minúscula que encuentre en el fichero que se le pase como parámetro por línea de comandos, entendiendo por *rotar* el cambio de
    - `'a'` por `'e'`
    - `'e'` por `'i'`
    - `'i'` por `'o'`
    - `'o'` por `'u'`
    - `'u'` por `'a'`
    
    De este modo, un fichero de entrada que contuviera este texto:
    > In an age when acronyms were popular, the Manchester Mark I was sometimes referred to as MADM (Manchester Automatic Digital Machine) or MUC (Manchester University Computer).
    
    produciría como salida este otro:
    > In en egi whin ecrunyms wiri pupaler, thi Menchistir Merk I wes sumitomis rifirrid tu es MADM (Menchistir Aatumetoc Dogotel Mechoni) ur MUC (Menchistir Unovirsoty Cumpatir).

3. Escriba un programa que lea un fichero de texto que se le pase como parámetro y produzca como salida ficheros con nombre `A.txt`, `B.txt`, ..., `Z.txt`. Cada uno de esos ficheros ha de contener, en líneas separadas, todas las palabras del fichero pasado como parámetro que comiencen por la correspondiente letra, mayúscula o minúscula.

4. Se conoce como [*cifrado César*](https://es.wikipedia.org/wiki/Cifrado_C%C3%A9sar) a un método muy simple de encriptación, consistente en sustituir cada carácter $n$ de un mensaje por el carácter $n+k$, siendo $k$ un valor entero. El siguiente sería un texto encriptado siguiendo este método y utilizando $k = 1:$
    ```
    Texto original:  Navidad, Navidad, dulce navidad
    Texto encriptado:  Obwjebe-!Obwjebe-!evmdf!obwjebe
    ```
    Se puede optar por hacer fijo el valor de $k$ o bien solicitarlo al usuario. Evidentemente, el desencriptado del fichero consistiría en realizar la operación inversa. En este caso, el valor de $k$ a utilizar debería solicitarse al usuario, para garantizar que éste está autorizado a leer el fichero.
    
    Desarrolle en C++ un programa cuya finalidad sea encriptar y desencriptar ficheros de texto. Deberá recibir por línea de comandos el nombre del fichero a procesar, el nombre del fichero de salida y el valor de $k.$ Por comodidad, puede permitir que el valor recibido de $k$ sea negativo, de forma que la encriptación y la desencriptación se realizarían mediante la misma operación, sólo cambiando el signo.
    ```
    $ ./cesar fichero_original.txt fichero_codificado.txt 3
    $ ./cesar fichero_codificado.txt fichero_decodificado.txt -3
    $ diff fichero_original.txt fichero_decodificado.txt
    ```
    En caso de detectar cualquier inconsistencia en los parámetros, el programa debe abortar su ejecución. Se mostrará asimismo un mensaje de error si el programa no consigue abrir el fichero de entrada.

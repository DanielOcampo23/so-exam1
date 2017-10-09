### Examen 1
**Universidad ICESI**  
**Curso:** Sistemas Operativos  
**Docente:** Daniel Barragán C.  
**Tema:** Comandos de Linux, Virtualización  
**Correo:** daniel.barragan at correo.icesi.edu.co

**Estudiante:** Daniel Steven Ocampo
**Código:** A00053980

### Objetivos
* Conocer y emplear comandos de Linux para la realización de tareas administrativas
* Virtualizar un sistema operativo
* Conocer y emplear capacidades de CentOS7 para la vitualización

### Prerrequisitos
* Virtualbox o WMWare
* Máquina virtual con sistema operativo CentOS7

### Descripción
El primer parcial del curso sistemas operativos trata sobre el manejo de los comandos de Linux, virtualización y el uso de las características de CentOS7

### Actividades
3. Resuelva los siguienes retos de la página https://cmdchallenge.com y presente la solución a cada uno de ellos a través de un ejemplo práctico en CentOS7. Presente capturas de pantalla relevantes como evidencias de lo realizado (20%)
  * sum_all_numbers
  * replace_spaces_in_filenames
  * reverse_readme
  * remove_duplicated_lines
  * disp_table

4. Realice un script que cumpla las condiciones que se describen a continuación. Presente capturas de pantalla relevantes como evidencias del funcionamiento (30%)
El usuario gutenberg debe existir en el sistema operativo
El script se debe ejecutar cada 5 minutos, consulte el manual de crontab
EL script debe descargar un libro del proyecto https://www.gutenberg.org/ en el directorio /home/gutenberg/mybooks
Si ya existe un libro en el directorio mybooks, debe ser reemplazado

5. Describa el funcionamiento del código fuente rickroll.c del repositorio de github https://github.com/jvns/kernel-module-fun. Muestre el funcionamiento al compilar el código y cargarlo como un módulo del kernel a través de un video que deberá cargar en Youtube e incluir el enlace en el informe (30%). Se recomienda emplear el sistema operativo Ubuntu con interfaz gráfica para esta prueba.

### Solución: 
3.  

* sum_all_numbers

Este reto consistía en que había un archivo .txt con una lista de números y nos pedían imprimir la suma de esa lista de números para la solución de este reto, ejecute la siguiente línea de código:

```
sum=0; while read line; do ((sum=$sum+$line)); done < sum-me.txt; echo $sum
```
Lo que hace esta línea de código, es crear una variable temporal "sum=0" después se hace un recorrido sobre esta lista leyendo cada línea de esta lista, y en cada iteración suma lo con que lleva en la variable "sum" con lo que hay en la línea ((sum=$sum+$line)) y a lo último imprime el resultado como muestra la siguiente imagen:

 ![GitHub Logo0](Images/Ejercicio1-suma2.png)
 
  * replace_spaces_in_filenames
  
  Este reto consiste en una lista de archivos con nombres de personas separadas con un espacio, y nos piden eliminar ese espacio y reemplazarlo por un punto para esto ejecute la siguiente linea de código:
  
```
  ls | sed 's/ /./g'
```

 Lo que hace "|" es que la salida del comando de la izquierda es entrada para el comando de la derecha, y el "sed" lo que hace es reemplazar dependiendo de los parámetros que se le ingresen en los slashs (/)
  
![GitHub Logo0](Images/ejercicio2-parte1.PNG)
 
![GitHub Logo0](Images/ejercicio2-parte2.PNG)




 * reverse_readme
 
 Este reto consiste en que hay un archivo.txt con varias líneas y en cada línea hay una frase, y nos piden imprimir cada línea pero recorriendo de manera contraria ósea al revés, esto es que la última línea en este archivo sea la primera en ser impresa y así sucesivamente hasta que la primera línea del archivo sea la última impresa.
 
 Para esto se ejecutó el siguiente comando

```
 tac README
```

El cual como se puede imaginar la palabra "tac" es la forma de decir "cat" pero al revés por lo que el funcionamiento de este comando "tac" es lo mismo que el del cat pero al reves (ósea imprimiendo desde la última línea del archivo hasta la primera) como lo ilustra su nombre.

![GitHub Logo0](Images/ejercicio3-parte1.PNG)

![GitHub Logo0](Images/ejercicio3-parte2.PNG)




 * remove_duplicated_lines
 
 Este reto consiste en que en un archivo .txt hay una lista de líneas en donde cada línea es una cadena con una secuencia de caracteres especiales, y muchas de estas líneas se repiten, por lo que nos piden imprimir únicamente una sola línea, y borrando las líneas que se repitan.
 
 Para esto ejecute el siguiente comando:

```
awk '!a[$0]++' faces.txt
```

![GitHub Logo0](Images/ejercicio4-parte1.PNG)

![GitHub Logo0](Images/ejercicio4-parte2.PNG)

Lo que hace este poderoso comando ``` awk ``` es algo parecido al comando ``` grep ``` y es buscar la palabra que se le envia por parametro dentro de todo el archivo, y retorna la cantidad de veces que encontró esta palabra, para esto el verifica la cantidad de veces que encontró esta palabra y si es mayor a una vez la imprime 



* disp_table

Este reto consiste en un archivo .txt contiene línea separadas con "," (comma-separated) y nos piden acomodarlo de esta manera como lo muestra en la imagen

![GitHub Logo0](Images/ejercicio4Descripcion.PNG)

Para esto ejecutamos el siguientes comando, el cual tabula las columnas y reemplazando la coma por los espacios requeridos 

```
column -s "," -t table.csv
```

![GitHub Logo0](Images/ejercicio5.PNG)




4.
Para la solución de este punto, se creó un usuario en el sistema operativo con el nombre "gutenberg" como se muestra en la imagen

![GitHub Logo0](Images/AgregandoUsuarioAlSistema.png)

Y aquí verificamos como el usuario ya se encuentra en el sistema operativo

![GitHub Logo0](Images/RevisandoUsuario.png)

Después consultando el manual de crontab, encontré como ejecutar un comando cada cierto periodo de tiempo que uno le determine, para el caso requerido del parcial, se le determinó ejecutarse cada 5 minutos. Ahora por motivos prácticos, no creí necesario crear un archivo .sh (script) ya que este nada más contaba con una sola línea ``` wget -q -O /home/gutenberg/mybooks/996.txt https://www.gutenberg.org/ebooks/996.txt.utf-8 ``` la cual descarga en el directorio especificado en este comando, y además en caso de existir anteriormente se sobrescribirá, por esta razón en el mismo crontab añadí esta línea de código en vez de la ejecución del Script.

Comando:

```
(crontab -l 2>/dev/null; echo "*/5 * * * * wget -q -O /home/gutenberg/mybooks/996.txt https://www.gutenberg.org/ebooks/996.txt.utf-8") | crontab -
```

Prueba de funcionamiento, aquí podemos detallar que en una imagen el libro fue descargado, y a los 5, 10 y 15 minutos después como fue descargado y reemplazado ya que existía anteriormente

![GitHub Logo0](Images/crontab1.png)


Minutos después.....


![GitHub Logo0](Images/crontab5.png)


5. 

Compilación del rickroll:

![GitHub Logo0](Images/makeModule.png)

Prueba de funcionamiento del rickroll.c:
https://youtu.be/oAfbTwwPymo


### Referencias ### 

https://youtu.be/oAfbTwwPymo

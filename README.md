# Taller inicial de compilación, ejecución y uso compartido de optimizadores

En el presente documento de presenta el desarrollo de los incisos del taller planteado

### 1. Compilacion y ejecucion de codigo de metodo jacobiano usando gcc

Para iniciar con el taller se accedio a el servidor haciendo uso de las credenciales de acceso asignadas y conexión remota a través de ssh. Una vez en el servidor se accedió a guane
y se hizo la reserva interactiva para trabajar haciendo uso del comando:

srun -n 2 --pty /bin/bash.

Para el desarrollo del primer punto, una vez realizada la reserva, se escribió el código referenciado en el taller sobre el método Jacobiano mediante el editor de texto por consola nano. Una vez creado el archivo del código, se compilo haciendo uso de gcc mediante el comando:

gcc jacobi.c -o jacobi

#### Resultado de la ejecución


### 2. Uso de las banderas -O1 -O2 -O3

Para el desarrollo de este segundo punto, se hizo uso de las banderas de optimización -o1 -o2 -o3 junto con el comando de compilación empleado en el segundo punto, los comando empleados fueron:

gcc -O1 jacobi.c -o jacobiejecutable01
gcc -O2 jacobi.c -o jacobiejecutable02
gcc -O3 jacobi.c -o jacobiejecutable03

#### Análisis de ejecución(tiempo)
    
| optimización | Tiempo ejecucion Guane user (s) |  Tiempo ejecucion Guane sys (s) |

|--------------|----------------------------------------|-----------------------|
| O1 			| 0m0.000s   	         | 0m0.001s   	         |
| O2 			| 0m0.000s  	         |0m0.001s   	         |
| O3  	    	| 0m0.000s 	                     |0m0.002s   	         |
| sin opt. 	    	| 0m0.001s 	                     |0m0.001s   	         |

Conforme aumenta el nivel de optimización (de -O1 a -O2 a -O3), generalmente se espera que el tiempo de ejecución disminuya. Esto se debe a que las optimizaciones más agresivas deberían producir un código más eficiente y, por lo tanto, reducir el tiempo de ejecución.
Esta tendencia es visible en tus resultados: el tiempo de ejecución disminuye de -O0 a -O1 a -O2. Sin embargo, la ejecución con -O3 parece haber resultado en un tiempo de ejecución significativamente más largo. Esto pudiera indicar que no siempre las optimizacion mas agresivas conducen a un mejor rendimiento.



#### Análisis de compilación

para analizar su compilación se empleó el comando: 

 objdump -d main -Mintel64

en donde se analizó la compilación tanto para el código sin optimizar como el optimizado y ver cómo fue construido por el compilador, de acá se puede ver a nivel de ensamblador que en el código optimizado, se han eliminado algunas instrucciones redundantes o innecesarias que no contribuyen a la lógica del programa. Por ejemplo, en el código no optimizado, hay algunas instrucciones de movimiento de datos que se han simplificado en el código optimizado. En el código optimizado, las instrucciones se han reorganizado para aprovechar al máximo el rendimiento del procesador y reducir el número de ciclos de reloj necesarios para completar una tarea.


### 3. Uso de las banderas -O -O0 -Og Oz

En este caso se usaron las banderas mencionadas. La bandera -O aplica una optimización dependiendo de los criterios del compilador, no se indica el nivel de agresividad, la bandera -O0 lo que hace es eliminar la optimización aplicada al código, la bandera -Og ayuda en la depuración del código corrigiendo algunos tipos de errores y la bandera -Oz intenta reducir el tamaño del código.


### 4. Analisis de codigo de internet

para el desarrollo del cuarto punto se implemento el codigo del metodo de biseccion el cual fue tomado del siguiente [enlace] (https://www.javatpoint.com/bisection-method-in-c). Seguidamente se desarrolló lo evidenciado en los puntos anteriores
pero ahora con este código el cual hace uso de punteros con el fin de analizar su rendimiento.

#### Análisis de ejecución

| optimización | Tiempo ejecucion Guane user (s) |  Tiempo ejecucion Guane sys (s) |

|--------------|----------------------------------------|-----------------------|
| O1 			| 0m0.001s   	         | 0m0.000s   	         |
| O2 			|0m0.001s  	         |0m0.000s   	         |
| O3  	    	| 0m0.001s  	                     | 0m0.001s   	         |
| sin opt. 	    	| 0m0.000s 	                     |0m0.002s   	         |

En general, el tiempo de ejecución del usuario parece ser muy bajo en todos los casos. Esto indica que la mayor parte del tiempo de CPU se dedica a la ejecución del código del usuario, los tiempos de ejecución del sistema también son bastante bajos en general. Esto indica que hay una baja cantidad de tiempo de CPU dedicada a las llamadas al sistema y otras tareas del sistema operativo durante la ejecución del programa. lo cual puede deberse a la implementación de punteros en el código,
Los tiempos de ejecución del usuario y del sistema son bajos en ambos casos, pero se puede ver que el tiempo total de ejecución puede variar significativamente entre la ejecución sin optimización y las ejecuciones con optimización. Esto puede indicar que las optimizaciones pueden mejorar el rendimiento general del programa
#### Análisis de compilación

El primer bloque (sin optimizar) contiene más operaciones de gestión de memoria explícitas, como mover datos entre registros y ubicaciones de memoria (mov).
Los otros bloques (optimizados) parecen estar más simplificados, con menos operaciones de gestión de memoria explícitas. Es posible que esté utilizando optimizaciones del compilador para reducir operaciones de memoria innecesarias.
Los bloques del código optimizado son más compactos, esto mejora la legibilidad 
Con el uso de las banderas -O -O0 -Og -Oz, la que tuvo mayor relevancia fue la bandera -Oz al reducir los bloques de código significativamente.

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

#### Análisis de ejecución
	
| optimización | Tiempo ejecucion Guane (s) |
|--------------|----------------------------------------|
| O1      	   | 1,000    	                            |
| O2      	   | 10,000   	                            | 
| O3   	       | 100,000  	                            | 

#### Análisis de compilacion

### 3. Uso de las banderas -O -O0 -Og Oz





### 4. Analisis de codigo de internet

para el desarrollo del cuarto puento se implemento el codigo del metodo de biseccion el cual fue tomado del siguiente [enlace] https://www.javatpoint.com/bisection-method-in-c. seguidamente, se desarrollo lo evidenciado en los puntos anteriores
pero ahora con este codigo el cual hace uso de punteros con el fin de analizar su rendimiento.

#### Análisis de ejecución

| optimización | Tiempo ejecucion Guane (s) |
|--------------|----------------------------------------|
| O1      	   | 1,000    	                            |
| O2      	   | 10,000   	                            | 
| O3   	       | 100,000  	                            | 





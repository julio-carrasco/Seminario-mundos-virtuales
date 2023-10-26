# seminario_mundos_virtuales
1- Qué funciones se pueden usar en los scripts de Unity para llevar a cabo traslaciones, rotaciones y escalados
translation para translaciones, rotation para rotaciones, transform.localScale para cambiar el tamaño


2- Como trasladarías la cámara 2 metros en cada uno de los ejes y luego la rotas 30º alrededor del eje Y?. Rota la cámara alrededor del eje Y 30ª y desplázala 2 metros en cada uno de los ejes. ¿Obtendrías el mismo resultado en ambos casos?. Justifica el resultado.

Para trasladar la cámara podemos usar translate y luego rotate que son métodos de transform, si alteramos el orden de la rotación y la traslación obtendremos resultados diferentes ya que la traslación se hace basándonos en los ejes locales del objeto por lo que al hacer la rotación primero y luego la traslación terminaremos en una posición diferente.


3- Sitúa la esfera de radio 1 en el campo de visión de la cámara y configura un volumen de vista que la recorte parcialmente.

Para esto podemos hacerlo de dos formas, la primera es aumentando el campo 
Near esto haría que la primera mitad de la esfera desapareciese, todo lo que estuviese a una distancia menor al campo Near de la cámara no aparecería, en cambio si disminuimos el campo Far lo que pasaría es que solo podemos ver los objetos que se encuentran entre el campo Near y el Far, si están demasiado lejos no se podrán ver.


4- Sitúa la esfera de radio 1 en el campo de visión de la cámara y configura el volumen de vista para que la deje fuera de la vista.

Para esto podemos o reducir el Far lo suficiente como para que la distancia desde la cámara sea mayor o podemos aumentar el Near lo suficiente para que este sea mayor que la distancia hasta la esfera.


5- Como puedes aumentar el ángulo de la cámara. Qué efecto tiene disminuir el ángulo de la cámara.

Para cambiar el ángulo de la cámara modificamos el fov, field of view, de la cámara, disminuirlo hace que el campo de visión de la cámara tenga un menor ángulo, es decir mostrará menos objetos, como si hiciese zoom.


6- Es correcta la siguiente afirmación: Para realizar la proyección al espacio 2D, en el inspector de la cámara, cambiaremos el valor de projection, asignándole el valor de orthographic.

Cuando cambiamos la cámara a modo ortográfico todos los objetos son del mismo tamaño sin importar la distancia a la cámara, es decir no hay distorsión por perspectiva y se ve con un efecto 2d


7- Especifica las rotaciones que se han indicado en los ejercicios previos con la utilidad quaternion.

Como se nos explica aquí: https://docs.unity3d.com/es/2019.4/Manual/QuaternionAndEulerRotationsInUnity.html para rotar un objeto usando la utilidad de los quaternions debemos hacer:
transform.rotation = Quaternion.Euler(0, 30, 0); Para rotar 30 grados alrededor del eje Y

8- ¿Como puedes averiguar la matriz de proyección en perspectiva que se ha usado para proyectar la escena al último frame renderizado?

Para acceder a la matriz de proyección en perspectiva de una cámara podemos usar el atributo projectionMatrix de un objeto Camera. Para averiguar la del último frame renderizado podemos poner un debug.log de la misma dentro de Update().

9- ¿Como puedes averiguar la matriz de proyección en perspectiva ortográfica que se ha usado para proyectar la escena al último frame renderizado?.

Para la matriz de proyección en perspectiva ortográfica se haría de la misma manera, solo que para que la cámara sea de perspectiva ortográfica, en el inspector tendremos que cambiar la opción de de “Projection” de “Perspective” a “Ortographic”

10- ¿Cómo puedes obtener la matriz de transformación entre el sistema de coordenadas local y el mundial?.

Para obtener la matriz de transformación entre el sistema de coordenadas local y el mundial existe la propiedad de transform, transform.localToWorldMatrix. Y la podemos guardar como un objeto Matrix4x4.

11- Cómo puedes obtener la matriz para cambiar al sistema de referencia de vista

La matriz para cambiar al sistema de referencia de vista se obtiene con la propiedad de camera, camera.worldToCameraMatrix. En Unity la matriz de vista se deriva de la posición y orientación de la camara.

12- Especifica la matriz de la proyección usado en un instante de la ejecución del ejercicio 1 de la práctica 1.

Matriz proyección:
1.45675	0.00000	0.00000	0.00000
0.00000	2.74748	0.00000	0.00000
0.00000	0.00000	-1.00080	-0.40016
0.00000	0.00000	-1.00000	0.00000


13- Especifica la matriz de modelo y vista de la escena del ejercicio 1 de la práctica 1.Matriz modelo:
0.99991	-0.00038	-0.01370	0.21370
0.00000	0.99961	-0.02781	1.40281
0.01371	0.02781	0.99952	-3.99952
0.00000	0.00000	0.00000	1.00000
Matriz vista:
0.99991	0.00000	0.01371	-0.15887
-0.00038	0.99961	0.02781	-1.29096
0.01370	0.02781	-0.99952	-4.03954
0.00000	0.00000	0.00000	1.00000

14- Aplica una rotación en el start de uno de los objetos de la escena y muestra la matriz de cambio al sistema de referencias mundial
Matriz antes de la rotación:
1.00000	0.00000	0.00000	8.41514
0.00000	1.00000	0.00000	2.09000
0.00000	0.00000	1.00000	-1.28000
0.00000	0.00000	0.00000	1.00000
            Matriz después de la rotación:
            0.87500	-0.21651	0.43301	8.41514
0.43301	0.75000	-0.50000	2.09000
-0.21651	0.62500	0.75000	-1.28000
0.00000	0.00000	0.00000	1.00000

15- ¿Como puedes calcular las coordenadas del sistema de referencia de un objeto con las siguientes propiedades del Transform:?: 
Position (3, 1, 1), Rotation (45, 0, 45)

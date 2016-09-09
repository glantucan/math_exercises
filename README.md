# Ejercicios de Matemáticas en Unity
Todo el material necesario para realizar los ejercicios están dentro esta misma carpeta de proyecto de Unity.

Cada ejercicio tiene una escena correspondiente en la carpeta Scenes dentro de Assets. Para trabajar en ese ejercicio abre su escena. Encontrarás un gameobject con una etiqueta con el nombre del ejercicio. Ese gameobject contiene un componente con el script en el que tienes que trabajar para completar el ejercicio. Los scripts también se llaman igual que el ejercicio para evitar confusiones.

No toques lo que hay en el resto de carpetas, salvo que te lo pida el enunciado del ejercicio. En algunos ejercicios hay ejemplos o código adicional que debes respetar si quieres que funcione todo correctamente cuando termines el ejercicio.



## Vectores

Los primeros ejercicios son para desarrollar la intuición sobre el sistema de coordenadas de Unity. Aunque me he preocupado de hacerlo difícil (para evitar tentaciones), siempre es posible hacer trampas para terminar los ejercicios rápido. Pero recuerda que la idea es que los ejercicios tienen un objetivo didáctico. Tenerlos terminados sin aprender no sirve de nada.
 
1. Posiciona cada cubo en su marcador correspondiente usando vectores 
y teniendo en cuenta que el marcador X se encuentra en el origen de coordenadas. 
Si la tienes desactivada, no olvides activar la rejilla de escena en *Guizmos* -> *Show Grid*, para que puedas estimar la posición de los marcadores con un mínimo de exactitud.
Utiliza la función `Start()` y las variables que ya están definidas e inicializadas en el script que está como componente del gameobject vectores_01.

  Ejemplo:
  ```cs
cube_3.transform.position = new Vector3 (1, 0, 3);
```
Tambien lo puedes hacer así:
  ```cs
cube_3.transform.position = 1*Vector3.right + 3*Vector3.forward;
```
  Usando los vectores unidad en las direcciones de los ejes: 
>   x -> Vector3.right 
>   y -> Vector3.up 
>   z -> Vector3.forward 

  Te recomiendo que lo hagas de las dos maneras por que dependiendo de la situación 
es más cómodo usar una o otra de las formas.

2. Haz como en el ejercicio anterior, pero en la escena *Vectores02*. Ahora entra en juego la coordenada y.

3. En este ejercicio tienes que hace que el cubo marcado con la X se de un punto a otro de la ruta marcada en el suelo. El cubo tiene un script con una función (`mover`) que permite hacer que se mueva con velocidad constante dándole como parámetro el vector de desplazamiento<sup>(1)</sup> como se ve en este ejemplo:
  
  ```cs
  void Start() {
      mover.SetInitialPosition(new Vector3(4, 0, -4));  // 1º fijamos la posición inicial del cubo.
	  mover.Move(-2 * Vector3.right); // Ordenamos al cubo que se mueva al punto 1 azul
	  mover.Move(5 * Vector3.forward); // Ordenamos al cubo que se mueva al punto 2 azul.
}
  ```
  > <sup>(1)</sup> El vector desplazamiento es el vector que va desde donde esté el cubo hasta el lugar donde tiene que moverse.
  > Aclaración: La función `Move()` no existe como tal en Unity. Es una función que he creado para estos ejercicios para que no te tengas que preocupar nada más que de lo básico de los vectores.

4. Utilizando la misma técnica que en el ejercicio anterior mueve el cubo X de un vértice a otro del paralelepípedo grande que hay en la escena siguiendo el orden indicado por los marcadores y empezando en la X. 
> Fíjate en que la textura del cubo tiene una rejilla: Las líneas más marcadas están separadas un metro entre sí.

5. En la escena Vectores05 haz que el cubo x se mueva por la superficie del bloque pasando por todas las esferas en el orden que quieras.  
  
  ---
  
  En muchos juegos el contenido de un nivel se genera al vuelo. En lugar de diseñar el escenario al completo en un Maya o similar y cargarlo entero se diseñan piezas modulares y se genera el nivel colocando esas piezas con cierta aleatoriedad o en un orden prefijado en un archivo de texto que sirve de mapa para generar el escenario. Esto tiene entre otras ventajas que la carga de cada nivel es mucho más rápida y que ocupamos menos memoria. 
  El siguiente bloque de ejercicios trabaja algunas técnicas usando bucles y vectores para generar geometría más o menos compleja a partir de prefabs.   

6. Utilizando el prefab **`[XXX]`**, genera una fila de 10 cubos consecutivos en la dirección x, empezando en la posición (-10, 0, 0)
	* Crea la escena Vectores06. 
    * Crea un GameObject vacío y llámalo Vectores06
	* Crea el script Vectores06 en la carpeta de scripts y escribe el código del ejercicio en él. 
	* En el bucle utiliza `GameObject.Instantiate()`<sup>(2)</sup> para crear clones del prefab 
	* Tendrás que calcular la coordenada x del vector de posición de cada cubo utilizando una fórmula muy simple utilizando el contador del bucle como variable. 
	
  ><sup>(2)</sup> Fíjate en que en la ayuda de Unity para muchas funciones aparecen varias versiones de la misma función con distintos parámetros.
  Eso significa que podemos utilizar la que más nos guste o convenga en cada momento.
  En este caso vamos a utilizar la primera. 
	```cs
	public GameObject cubePrefab;
	//...
	void Start() {
		//...
		GameObject cubeInstance = Object.Instantiate(cubePrefab);
		cubeInstance.transform.position = ...
		//...
	} 
    ```
	**Cuidado**: Los ejemplos de la página de Unity no siempre son muy claros y es fácil que te confundan si no entiendes bien la diferencia entre lo que hacen y lo que tú quieres hacer.
7. Repite el ejercicio anterior pero genera la fila de cubos en la dirección z. Haz que empiece en la posición (-10, 0.5, -10).
  
  > A partir de ahora, aunque no se mencione en el escenario para cada ejercicio debes crear una nueva escena, con el nombre del tema seguido del número de ejercicio (en este caso será: Vectores07) y su correspondiente gameobject con el mismo nombre para colocar el script del ejercicio (también con el mismo nombre).

8. RETO: Haz una fila de cubos en diagonal utilizando el mismo prefab sin modificar que en los ejercicios anteriores. Hay varias formas. Una de ellas es usar la propiedad `normalized` de los vectores.
  
9. Repite los ejercicios 6 y 7 dejando 2, y 3 espacios entre los cubos, respectivamente.
10. Construye una escalera de cubos, pero alternando clones del prefab **`[XXX]`** y **`[YYY]`**.
> Podrías hacerlo utilizando dos bucles, pero puedes hacerlo si recuerdas o aprendes a usar el operador módulo: `%`. La expresión: 
  ```cs 
  int resto = 7 % 2
  ```
> Devuelve le resto de la división entera de `7` entre `2`. Es decir, el resultado de la división sería `3`, dejando un resto de `1`. O sea que `resto` tendría el valor `1`.



## Vectores y proporcionalidad
Tenemos la suerte de que hay un montón de situaciones en la vida real que podemos simular en videojuegos con una simple relación de proporcionalidad.

**Ejemplo:**
La velocidad (cuando es constante, o hablamos de velocidad media) es una relación de proporcionalidad entre el espacio recorrido y el tiempo que se tarda en recorrerlo. Cuando un objeto se mueve 5 metros en 2 segundos, si sabemos que su velocidad es constante, y queremos saber cuanto tardará en recorrer 20 metros, o sea 4 veces esa distancia, sabemos que tenemos que multiplicar el tiempo por ese mismo número: 4.  

Si queremos usar la velocidad para calcular la distancia que se recorre en un tiempo determinado, es mucho más cómodo expresarla como los metros que se recorren en 1 segundo. En el ejemplo anterior sería 5/2 m/s = 2.5 m/s, ose 2.5 metros en 1 segundo.
 
Así si multiplicamos los segundos por 15, osea, queremos saber el espacio recorrido en 15 segundos, sólo tenemos que multiplicar el valor de los metros por 15 en la velocidad: 2.5 · 15 = 37.5 metros recorridos en 15 segundos.
 
Podemos hacer esta cuenta sencilla porque sabemos que en este tipo de situación (velocidad constante) la distancia recorrida es proporcional a la velocidad y al tiempo transcurrido. (s = v·t)

**Fíjate** en que allí donde hay una relación de proporcionalidad, también hay una relación de proporcionalidad inversa. 

El tiempo que tardas en recorrer una determinada distancia es proporcional a la distancia, pero inversamente proporcional a la velocidad: a más velocidad, menos tiempo.  (t = s/v)

---

Normalmente no hacemos todo este razonamiento porque estamos muy acostumbrados a pensar en velocidades, pero lo importante es que seas capaz de reconocer la proporcionalidad entre dos cantidades y aplicar el razonamiento anterior a cualquier situación en la que haya una relación de proporcionalidad.
	
* En un videojuego el daño que te hace estar en una zona radiactiva o con una atmósfera ácida es porporcional al tiempo que pasas en ella, o dándole la vuelta el tiempo que puedes pasar en una atmósfera nociva es inversamente proporcinal a los puntos de daño que te quita por segundo.
* El número de pociones de vida que puedes comprar en el mercadillo del mago es proporcional al dinero que tienes, e inversamente proporcional al precio de cada poción de vida.
* Cuando se genera una escena proceduralmente hay que usar relaciones de proporcionalidad constantemente para colocar los objetos en el escenario:
	* El número de baldosas que caben en una habitación es direcatmente proporcional al tamaño de la misma, e inversamente proporcional al tamaño de la baldosa.  
	* El número de escalones que tiene una escalera es proporcional a la altura de la misma e inversamente proporcional a la altura del escalón.
	* ...

* El tiempo transcurrido desde el inicio del juego en un Update() es proporcional al numero de fotogramas reproducidos y a la duración de cada fotograma (aunque en este caso sea mejor medirlo de otras formas).

Los siguientes ejercicios sirven para practicar en el reconocimiento y resolución de situaciones y problemas en los que la proporcionalidad juega un papel importante. Como para colocar y mover cosas en el espacio se trabaja con vectores en la mayoría de los caso tendrás que combinar estos razonamientos con los trabajados en los ejercicios anteriores.

---

1. Construye el segundero de un reloj
2. Construye el minutero al ejercicio anterior (prop angulos/tiempo)
2. Construye un reloj digital (prop entre seg/min/horas)
3. Añade al resultado del ejercicio anterior la aguja de las horas
4. Construye una escena simple con prefabs de tamaño fijo (usar meshrenderer para medir tamaños)
5. Barra de daño
6. Alcanza al otro PNJ en 5 segundos
7. Tiro al plato
8. Tiro al plato 2D
9. Tiro al plato 3D
10. Rodando
11. Adaptar la escala de un cubo a la textura.
12. Tiro parabólico con ángulo fijo (tirachinas) calcula velocidad para alcanzar al blanco

## Funciones matemáticas en `Matfh` y `Vector3`
No todas, decidir cuales son las más interesantes para su nivel.
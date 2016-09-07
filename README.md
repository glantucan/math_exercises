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

3. En este ejercicio tienes que hace que el cubo marcado con la X se de un punto a otro de la ruta marcada en el suelo. El cubo tiene un script con una función (`mover`) que permite hacer que se mueva con velocidad constante dándole como parámetro el vector de desplazamiento (*) como se ve en este ejemplo:
  
  ```cs
  void Start() {
      mover.SetInitialPosition(new Vector3(4, 0, -4));  // 1º fijamos la posición inicial del cubo.
	  mover.Move(-2 * Vector3.right); // Ordenamos al cubo que se mueva al punto 1 azul
	  mover.Move(5 * Vector3.forward); // Ordenamos al cubo que se mueva al punto 2 azul.
}
  ```
  > (*): El vector desplazamiento es el vector que va desde donde esté el cubo hasta el lugar donde tiene que moverse.
  > Aclaración: La función `Move()` no existe como tal en Unity. Es una función que he creado para estos ejercicios para que no te tengas que preocupar nada más que de lo básico de los vectores.

4. Utilizando la misma técnica que en el ejercicio anterior mueve el cubo X de un vértice a otro del paralelepípedo grande que hay en la escena siguiendo el orden indicado por los marcadores y empezando en la X. 
> Fíjate en que la textura del cubo tiene una rejilla: Las líneas más marcadas están separadas un metro entre sí.

5. Otro más laberíntico.
6. Sucesión infinita* de cubos. 
7. Pared de cubos.
8. Calcula la dirección en que hay que moverse.
9. 

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

1. Construlle el segundero de un reloj
2. Construlle el minutero al ejercicio anterior (prop angulos/tiempo)
2. Construlle un reloj digital (prop entre seg/min/horas)
3. Añade al resultado del ejercicio anterior la aguja de las horas
4. Construlle una escena simple con prefabs de tamaño fijo (usar meshrenderer para medir tamaños)
5. Barra de daño
6. Alcanza al otro PNJ en 5 segundos
7. Tiro al plato
8. Tiro al plato 2D
9. Tiro al plato 3D
10. Rodando
11. Adaptar la escala de un cubo a la textura.
12. Tiro parabólico con ángulo fijo (tirachinas) calcula velocidad para alcanzar al blanco
13. 
	
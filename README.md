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
>  Ejemplo:
  ```cs
cube_3.transform.position = new Vector3 (1, 0, 3);
```
Tambien lo puedes hacer así:
  ```cs
cube_3.transform.position = 1*Vector3.right + 3*Vector3.forward;
```
Usando los vectores unidad en las direcciones de los ejes: 
>&nbsp;&nbsp;&nbsp;&nbsp;   x -> Vector3.right 
>&nbsp;&nbsp;&nbsp;&nbsp;   y -> Vector3.up 
>&nbsp;&nbsp;&nbsp;&nbsp;   z -> Vector3.forward 
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
  
  > A partir de ahora, aunque no se mencione en el enunciado, para cada ejercicio debes crear una nueva escena, con el nombre del tema seguido del número de ejercicio (en este caso será: Vectores07) y su correspondiente gameobject con el mismo nombre para colocar el script del ejercicio (también con el mismo nombre).

8. RETO: Haz una fila de cubos en diagonal utilizando el mismo prefab sin modificar que en los ejercicios anteriores. Hay varias formas. Una de ellas es usar la propiedad `normalized` de los vectores. Otra pasa por colocar las instancias como hijas un Gameobject vacío y rotar después éste último. ¿Se te ocurre alguna otra?
  
9. Repite los ejercicios 6 y 7 dejando 2, y 3 espacios entre los cubos, respectivamente.
10. Construye una escalera de cubos.  

11. Construye una escalera de cubos, pero alternando clones del prefab **`[XXX]`** y **`[YYY]`**.

 > Podrías hacerlo utilizando dos bucles, pero puedes hacerlo si recuerdas o aprendes a usar el operador módulo: `%`. La expresión:  
 ```cs 
  int resto = 7 % 2
  ```
 > Devuelve le resto de la división entera de `7` entre `2`. Es decir, el resultado de la división sería `3`, dejando un resto de `1`. O sea que `resto` tendría el valor `1`.
12. Construye una escalera de cubos dejando descansillos (con instancias del prefab *StairLanding*) cada 5 escalones.  

13. Repite el ejercicio anterior, pero creando tú, tus propios prefabs de escalón y de descansillo<sup>(3)</sup> a  partir de la primitiva de un cubo  de Unity. ¿Por qué no funciona bien tu script del ejercicio anterior?. Arregla el script para estos nuevos prefabs.
><sup>(3)</sup> Crea una carpeta Vectores13 en la capeta de Prefabs y coloca ahí los que crees para este ejercicio. Haz lo mismo en todos los ejercicios en los que necesites crear prefabs.

14. Ahora que te manejas mejor con los vectores vas a hacer que un gameobject se mueva con velocidad constante en la direccion x. Para eso tenemos que usar la función `Update()`. Lo que harás es actualizar la posición del gameobject basándote en el valor numérico de una propiedad que llamarás `v` y que debes declarar como pública para que se pueda rellenar desde el inspector. La velocidad introducida se interpretará como que está en m/s.
En cada fotograma, a la posición actual del gameobject le sumaras su velocidad multiplicada por el tiempo transcurrido desde el ultimo *update* <sup>(4)</sup> en la dirección x. 
 ><sup>(4)</sup> Recuerda que en un movimento rectilineo y con velocidad uniforme 
 > s = v·t
 >donde s es el espacio recorrido, v es la velocidad y t el tiempo transcurrido.
 >Puedes leer el tiempo transcurrido desde el fotograma anterior con la propiedad `Time.deltaTime`.

15. Repite el ejercicio anterior pero en vez de mover el gameobject en la dirección x, hazlo en la dirección dada por un vector que se introduzca también en el inspector. 
Para evitar que la velocidad a la que se mueve el gameobject dependa de la longitud del vector introducido, normaliza el vector utilizando su propiedad `normalized`

16. RETO: Repite el ejercicio 15, pero en vez de utilizar un vector para indicar la dirección usa dos ángulos. Uno (de 0 a 360 grados) para el ángulo en el plano horizontal y otro (de -90 a 90) para indicar la inclinación vertical. 
>Tendrás que usar las funciones `Mathf.Sin()`, `Mathf.Cos()` y convertir los ángulos a radianes utilizando la propiedad `Mathf.DegToRad` (porque las funciones anteriores requieren que les pases el ángulo en radianes).
>***Más información:***  *Estos dos ángulos, junto con la longitud del vector  son lo que se denomina sistema de coordenadas polares, mientras que el que usamos normalmente se denomina sistema cartesiano. <br>Ambos sistemas son válidos y útiles dependiendo de la situación, A pesar de que Unity use el sistema cartesiano para manejar vectores, en algánas mecánicas de juego nos puede interesar utilizar coordenadas polares, aunque después haya que convertirlas a cartesianas.*

17. Abre la escena Vectores17 y ejecútala. Verás una esfera que se mueve con velocidad constante. Cada vez que ejecutes a escena se moverá en una dirección diferente. Tienes que hacer que el cubo con la X persiga a la esfera con velocidad constante (usa la misma propiedad pública, `v`, que en el ejercicio anterior, dándole un valor de 2 en el inspector). Ahora, en lugar de introducir la dirección en el inspector, tienes que hacer que tu programa la calcule teniendo en cuenta la posición del cubo y la posición de la esfera objetivo en cada instante.  
18. Repite el ejercicio anterior pero en vez de introducir la velocidad del cubo en el inspector haz que tu programa calcule la velocidad del target y la iguale. Tu programa debe calcularla observando su posición en el primer y segundo fotogramas. (Utiliza dos condicionales y una propiedad que cuente los fotogramas para esto) 
> Recuerda que el el target tiene una velocidad constante, por lo que v = s/t.

19. Ahora, haz que tu programa estime la posición del target después de 5 segundos y ajuste la velocidad del cubo de forma que lo alcance en esa posición.

20. Construye el segundero de un reloj. Utiliza un cilindro para el cuerpo del reloj y un cubo deformado para hacer de segundero, puedes utilizar un gameobject vacío adicional como padre del segundero, para que haga de pivote de giro del mismo). La aguja debe rotar los grados que sean necesarios de golpe cuando transcurra cada segundo, no de forma continua.

21. Añade el minutero al reloj del ejercicio anterior. El minutero debe rotar los grados correspondientes a un minuto también de golpe, cuando el segundero haya completado una circunferencia completa.

22. Termina el reloj con la aguja de las horas. Esta aguja debe rotar de forma continua, actualizando su posición en cada fotograma.

23. Añadir texturas a las agujas. Puedes encontrarlas en la carpeta *Textures* del proyecto. Adapta la escala de los cubos de las agujas a las texturas que se proporcionan, para que no estén deformadas. Fíjate en la escala que tienes que darle a los cubos en cada dirección para cumplir esta condición. ¿Cómo podrías haberlas calculado para escrivir esos valores a la primera, en lugar de a ojo?

5. Barra de daño
7. Tiro al plato
8. Tiro al plato 2D
9. Tiro al plato 3D
10. Rodando
12. Tiro parabólico con inclinación fija (tirachinas). Calcula la velocidad para alcanzar al blanco

## Funciones matemáticas en `Random`, `Matfh` y `Vector3`
No todas, decidir cuales son las más interesantes para su nivel y pensar ejercicios.

* Redondeos
* Trigonometría
* Clamp
* Lerp


# Ejercicios de Matemáticas en Unity
Todo el material necesario para realizar los ejercicios están dentro esta misma carpeta de proyecto de Unity.

Cada ejercicio tiene una escena correspondiente en la carpeta Scenes dentro de Assets. Para trabajar en ese ejercicio abre su escena. Encontrarás un gameobject con una etiqueta con el nombre del ejercicio. Ese gameobject contiene un componente con el script en el que tienes que trabajar para completar el ejercicio. Los scripts también se llaman igual que el ejercicio para evitar confusiones.

No toques lo que hay en el resto de carpetas, salvo que te lo pida el enunciado del ejercicio. En algunos ejercicios hay ejemplos o código adicional que debes respetar si quieres que funcione todo correctamente cuando termines el ejercicio.



## Vectores


1. Posiciona cada cubo en su marcador correspondiente usando vectores 
y teniendo en cuenta que el marcador X se encuentra en el origen de coordenadas. Utiliza la función `Start()` y las variables que ya están definidas e inicializadas en el script que está como componente del gameobject vectores_01.

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
es más comodo usar una o otra de las formas



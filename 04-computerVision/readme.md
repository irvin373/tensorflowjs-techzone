# 4. Mobile Net

Durante la parte final del workshop haremos una prueba de mobile net.

## Estructura del proyecto

lo primero que vamos a hacer es crear un nuevo proyecto y lo haremos de la siguiente manera:
[Descargar Proyecto](https://drive.google.com/open?id=1dnd8p19G_7eSeOOasgu54rF9ijwxIlNf)


> para correr el proyecto `yarn watch` o `npm run watch` levantara el proyecto.

> Ahora explicaremos algunas partes importantes ...

```
antes de comenzar es cargar el modelo previamente entrenado.

mobilenet = await tf.loadModel(MOBILENET_MODEL_PATH)

si necesitas mas inforamcion sobre los modelos: 
```
[importar modelos de keras](https://js.tensorflow.org/tutorials/import-keras.html)

[Guardar modelo en tf.Model](https://js.tensorflow.org/tutorials/model-save-load.html)
# Gracias por estar hasta el final del codelab
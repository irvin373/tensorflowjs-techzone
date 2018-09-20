# 3. Conceptos básicos

Ahora trabajaremos sobre un proyecto base para agregar funcionalidad en medio de todo el camino
[descarga el proyecto base](https://drive.google.com/open?id=1UbyiQm1uzb6YfQHWw8FaBeezZC-kLBQ3)
## Props

Las propiedades se pasan desde un componente padre hacia sus hijos. Donde el hijo podra acceder a estas mediante `this.props` que es un objeto inmutable.

### Button

tratemos de agregar una propiedad al boton reemplazando `soy un boton` por  `{this.props.option}`

### Board Game

ahora haremos lo siguiente en el archivo `Board.js` dentro de la funcion render haremos: `let {questions, header, answer} = this.props` lo cual asignaremos las propiedades a variables para poder usarlas donde `header` tomara lugar de `pregunta` y luego copien el siguiente codigo

```
{questions.map(item =>
  <ContentBtn key={item.id}
  id={item.id}
  answer={answer} option={item.option}
  />)
}
```

donde `questions` es un Array y tenemos que convertirlo en componentes botones es por eso que iteramos con una funcion que mapea a componente `ContentBtn`

### State

Ahora haremos los cambios que pueden ocurrir durante el live circle del proyecto. Recodar que el estado es de solo lectura si quiere hacerse un cambio sobre el mismo es mediante la funcion `setState`

en el `boardjs` haremos lo siguiente:

- crearemos el estado inicial del componente asi que 
```
this.state = {
  percent: 100,
  noTime: false
}
```
dentro del constructor.

- dentro de la funcion render agregaremos `let {percent, noTime} = this.state`  y tambien `let time = this.contador(percent)` - `this.runProgess()` para crear un contador de tiempo para terminar la trivia agregaremos un progress bar `<Progress percent={percent} indicating size='large' />` en el retorno de la funcion y a ver el resultado
y ahora agregamos `<p style={{fontSize: 25}}>{time}</p>` para mostrar un contador de tiempo.

## Events

Ahora pasaremos funciones para que puedan actualizar los estados.

## Gracias por asistir al workshop

Una vez terminado el workshop, se agradece completar la [encuesta](https://docs.google.com/forms/d/e/1FAIpQLSenK_TDn54NEv65PKyoGr9L4Us7x8y1Wdwzt7cw6BkR5HIBqA/viewform?usp=pp_url&entry.1506216363) para poder mejorarlo. También se aceptan [issues]
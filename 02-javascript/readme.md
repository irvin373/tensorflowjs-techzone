# 2. Ejecutando Promises en Javascript

La primera parte del codelab será iniciar promesas en javascript ya que al usar webGL y algunas operaciones asíncronas en necesario entender cómo funcionan para usar tensorflowjs

## Crear un archivo html js.

lo primero que vamos a hacer es crear un nuevo proyecto y lo haremos de la siguiente manera:

1. Primero crearemos un nuevo archivo html con la siguiente estructura
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title>Promises in js</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<body>
    <h1>Promesas en JS</h1>
    <script src="main.js"></script>
</body>
</html>
```

2. Lo siguiente será crear un archivo llamado main.js en javascipt.

```
function asincrono() {
    console.log('primera instruccion')
    setTimeout(() => {
        console.log('segunda instruccion')
    }, 1000)
    console.log('tercera instruccion')
}
asincrono()
```
 mandamos hacemos correrlo en el navegador.

3. Promesas en Javascipt.

```
function imprimirPromesa(msg, delay) {
	return new Promise( (resolve, reject) => {
    if(msg === 'error') {
      reject(msg)
    }
		setTimeout(() => {
			resolve(msg)
		}, delay)
	})
}

function imprimirPromesa(msg = 'segunda instruccion') {
    console.log('primera instruccion')
    imprimirPromesa(msg, delay).then(data => {
        console.log(data)
        console.log('tercera instruccion')
    }).catch(error => {
      console.error(error)
    })
}
imprimirPromesa()
//imprimirPromesa('error')
```
 mandamos hacemos correrlo en el navegador.

4. Promesas con async y await.

```
function imprimirPromesa(msg, delay) {
	return new Promise( (resolve, reject) => {
    if(msg === 'error') {
      reject(msg)
    }
		setTimeout(() => {
			resolve(msg)
		}, delay)
	})
}

async function imprimirPromesa(msg = 'segunda instruccion') {
    try {
      console.log('primera instruccion')
      let msg = await imprimirPromesa(msg, delay)
      console.log(msg)
      console.log('tercera instruccion')
    } catch(error) {
      console.error(error)
    }
}
imprimirPromesa()
// imprimirPromesa('error')
```
 mandamos hacemos correrlo en el navegador.

     > **Nota**: async y await son implementación que aún no todos los navegadores tienen soporte por lo cual la compatibilidad, es ayudada por transpiradores o polyfills.

5. Para esta parte copiar y ver los resultados en el navegador. 

```
let obj = {name: 'Kailina'}
let objFreeze = {name: 'Kailina'}
Object.freeze(objFreeze)
console.log(obj, objFreeze)
obj.edad = 7
objFreeze.edad = 7
console.log(obj, objFreeze)
obj.phone = 79356
objFreeze.phone = 79356
console.log(obj, objFreeze)
delete obj.phone
delete objFreeze.phone
console.log(obj, objFreeze)
```
 mandamos hacemos correrlo en el navegador.

6. Correr WebGl 

> a continuación mostraremos un código ejemplo para dibujar un canvas con fondo oscuro usando GPU de la máquina. ya que tensorflow js usa el GPU para varias operaciones matemáticas
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title>Page Title</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" type="text/css" media="screen" href="main.css" />
  <script src="main.js"></script>
</head>
  <body onload="start()">
    <canvas id="glcanvas" width="640" height="480">
    
        Tu navegador parece no soportar el elemento HTML5 <code>&lt;canvas&gt;</code>.
    </canvas>
      <script>
   function initWebGL(canvas) {
  gl = null;
  
  try {
    // Tratar de tomar el contexto estandar. Si falla, retornar al experimental.
    gl = canvas.getContext("webgl") || canvas.getContext("experimental-webgl");
  }
  catch(e) {}
  
  // Si no tenemos ningun contexto GL, date por vencido ahora
  if (!gl) {
    alert("Imposible inicializar WebGL. Tu navegador puede no soportarlo.");
    gl = null;
  }
  
  return gl;
}
var gl; // Un variable global para el contexto WebGL

function start() {
  var canvas = document.getElementById("glcanvas");

  gl = initWebGL(canvas);      // Inicializar el contexto GL
  
  // Solo continuar si WebGL esta disponible y trabajando
  
  if (gl) {
    gl.clearColor(0.0, 0.0, 0.0, 1.0);                      // Establecer el color base en negro, totalmente opaco
    gl.enable(gl.DEPTH_TEST);                               // Habilitar prueba de profundidad
    gl.depthFunc(gl.LEQUAL);                                // Objetos cercanos opacan objetos lejanos
    gl.clear(gl.COLOR_BUFFER_BIT|gl.DEPTH_BUFFER_BIT);      // Limpiar el buffer de color asi como el de profundidad
  }
}
gl.viewport(0, 0, canvas.width, canvas.height);

  </script>
</body>
</html>
```
## Próximo módulo
Avanzar al [módulo 3](../03-tensorflowjs)
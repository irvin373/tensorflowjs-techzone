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

2. Lo siguiente sera crear un archivo llamado main.js en javascipt.

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
		setTimeout(() => {
			resolve(msg)
		}, delay)
	})
}

function imprimirPromesa() {
    console.log('primera instruccion')
    imprimirPromesa('segunda instruccion', delay).then(data => {
        console.log(data)
        console.log('tercera instruccion')
    })
}
imprimirPromesa()
```
 mandamos hacemos correrlo en el navegador.

3. Promesas con async y await.

```
function imprimirPromesa(msg, delay) {
	return new Promise( (resolve, reject) => {
		setTimeout(() => {
			resolve(msg)
		}, delay)
	})
}

async function imprimirPromesa() {
    console.log('primera instruccion')
    let msg = await imprimirPromesa('segunda instruccion', delay)
    console.log(msg)
    console.log('tercera instruccion')
}
imprimirPromesa()
```
 mandamos hacemos correrlo en el navegador.

     > **Nota**: async y await son implementacion que aun no todos los navegadores tienen soporte por lo cual la compativilidad, es ayudada por transpiladores o polyfills.

## Próximo modulo
Avanzar al [módulo 3](../03-tensorflowjs)
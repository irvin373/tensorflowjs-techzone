# 3. Conceptos básicos Tensorflow


## Predecir funcion lineal
```
<!DOCTYPE>
<html>
<head></head>
<body>
 <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@0.13.0"> </script>
 <script src="main.js"></script>
</body>
</html>
```

## Tensor

![Tensor](./images/tensors.jpeg "Tensor")
  _Tensor_

 > Ahora si usaremos tensorflow para predecir una funcion lineal `Y = 2X - 1` y para comparar las predicciones usaremos la funcion original en javascript `const funcY = (item) => item * 2 - 1` Estos son los datos con los cuales comenzaremos la funcion 

>`const xs = tf.tensor2d([-1, 0, 1, 2, 3, 4], [6, 1])`
>`const ys = tf.tensor2d([-3, -1, 1, 3, 5, 7], [6, 1])`

### codigo para predecir la ecuacion
```
const funcY = (item) => item * 2 - 1

async function learnLinear () {
  const model = tf.sequential()
  model.add(tf.layers.dense({units: 1, inputShape: [1]}))
  model.compile({
    loss: 'meanSquaredError',
    optimizer: 'sgd'
  })

  const xs = tf.tensor2d([-1, 0, 1, 2, 3, 4], [6, 1])
  const ys = tf.tensor2d([-3, -1, 1, 3, 5, 7], [6, 1])

  await model.fit(xs, ys, {epochs: 500})
  let toPredict = [2, 10, 12, 5, 7]
  let output = document.getElementById('output_field')
  for (let item of toPredict) {
    let result = model.predict(tf.tensor2d([item], [1, 1]))
    console.log(`${item} -> ${result}`)
    output.innerHTML += `<p> valor ${item} - ${result} - valor Real ${funcY(item)}</p>`
  }
}
learnLinear()
```

## XOR

![XOR](./images/xor.png "XOR")

    _XOR_


```
async function predictOutput () {
  const model = tf.sequential()
  model.add(tf.layers.dense({ units: 8, inputShape: 2, activation: 'tanh' }))
  model.add(tf.layers.dense({ units: 1, activation: 'sigmoid' }))
  model.compile({ optimizer: 'sgd', loss: 'binaryCrossentropy', lr: 0.1 })
  // Creating dataset
  const xs = tf.tensor2d([[0, 0], [0, 1], [1, 0], [1, 1]])
  xs.print()
  const ys = tf.tensor2d([[0], [1], [1], [0]])
  ys.print()
  // Train the model
  await model.fit(xs, ys, {
    batchSize: 1,
    epochs: 5000
  })
  document.getElementById('output').innerText = model.predict(xs)
}
predictOutput()
```

## Próximo módulo
Avanzar al [módulo 4](../04-computerVision)

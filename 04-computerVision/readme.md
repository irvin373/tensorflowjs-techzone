# 4. Mobile Net

Durante la parte final del workshop haremos una prueba de mobile net.

## Estructura del proyecto

Crearemos un nuevo proyecto con el siguiente codigo ...

```
<html>
  <head>
    <!-- Load the latest version of TensorFlow.js -->
    <script src="https://unpkg.com/@tensorflow/tfjs"></script>
    <script src="https://unpkg.com/@tensorflow-models/mobilenet"></script>
  </head>
  <body>
    <video autoplay playsinline muted id="webcam" width="224" height="224"></video>
    <div id="console"></div>
    <!-- Load index.js after the content of the page -->
    <script src="index.js"></script>
  </body>
</html>
```
__index.html__

```
let net;
const webcamElement = document.getElementById('webcam');
async function setupWebcam() {
  return new Promise((resolve, reject) => {
    const navigatorAny = navigator;
    navigator.getUserMedia = navigator.getUserMedia ||
        navigatorAny.webkitGetUserMedia || navigatorAny.mozGetUserMedia ||
        navigatorAny.msGetUserMedia;
    if (navigator.getUserMedia) {
      navigator.getUserMedia({video: true},
        stream => {
          webcamElement.srcObject = stream;
          webcamElement.addEventListener('loadeddata',  () => resolve(), false);
        },
        error => reject());
    } else {
      reject();
    }
  });
}

async function app() {
  console.log('Loading mobilenet..');

  // Load the model.
  net = await mobilenet.load();
  console.log('Sucessfully loaded model');
  
  await setupWebcam();
  while (true) {
    const result = await net.classify(webcamElement);

    document.getElementById('console').innerText = `
      prediction: ${result[0].className}\n
      probability: ${result[0].probability}
    `;

    // Give some breathing room by waiting for the next animation frame to
    // fire.
    await tf.nextFrame();
  }
}

app();
```
__index.js__

si necesitas mas inforamcion sobre los modelos: 
```
[importar modelos de keras](https://js.tensorflow.org/tutorials/import-keras.html)

[Guardar modelo en tf.Model](https://js.tensorflow.org/tutorials/model-save-load.html)
# Gracias por estar hasta el final del codelab
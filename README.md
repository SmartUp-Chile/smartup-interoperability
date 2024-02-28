# SmartUp Interoperability Guide

How to detect special events from the SmartUp Agent portal to the platform window.

## The Strainer

Using the `message` event we can detect the events of chat started and data sent to the Strainer Database. Use this snippet to set up a Pixel event

```js
  <script>
    window.addEventListener('message', function (event) {
      if (event.data === 'chatStarted') {
        console.log('Evento cuando el chat se inicia');
        // TODO: Fire Pixel event...
      }

      if (event.data === 'dataSentToStrainerDb') {
        console.log('Evento cuando se envía la información a la base de datos de The Strainer')
        // TODO: Fire Pixel event...
      }
    });
  </script>
```

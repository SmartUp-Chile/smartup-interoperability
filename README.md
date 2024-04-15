# SmartUp Interoperability Guide

How to detect special events from the SmartUp Agent portal to the platform window.

## Global

### Hyperparameters

In order to insert special information into the agent, without the need of the user in specifying it, we can use Hyperparameters by adding new GET parameters to the URL.

```html
  https://www.smartup.lat/agente/[AGENT_ID]?[PARAMETER_1]=[VALUE_1]&[PARAMETER_2]=[VALUE_2]
```

## The Strainer

### Detect Pixel events

Using the `message` event we can detect the events of chat started and data sent to the Strainer Database. Use this snippet to set up a Pixel event

```js
  <script>
    window.addEventListener('message', function (event) {
      if (event.data === 'chatStarted') {
        console.log('Evento cuando el chat se inicia');
        // TODO: Fire Pixel event...
      }

      if (event.data === 'querySearch') {
        console.log('Evento para buscar candidatos');
        // TODO:
      }

      if (event.data === 'dataSentToStrainerDb') {
        console.log('Evento cuando se envía la información a la base de datos de The Strainer')
        // TODO: Fire Pixel event...
      }
    });
  </script>
```

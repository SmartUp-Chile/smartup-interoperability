# SmartUp Interoperability Guide

Karpathy was here! 🤖

How to detect special events from the SmartUp Agent portal to the platform window.

## Global

### Hyperparameters

In order to insert special information into the agent, without the need of the user in specifying it, we can use Hyperparameters by adding new GET parameters to the URL.

```html
  https://www.smartup.lat/agente/[AGENT_ID]?[PARAMETER_1]=[VALUE_1]&[PARAMETER_2]=[VALUE_2]
```

For example:

```html
  https://www.smartup.lat/agente/moishele?name=Daniel
```

#### How to use Hyperparameters-in-prompt?

Once you added the hyperpameters on the link, you need to edit the system prompt and type it like this:

```
{{PARAMETER_1}}
```

For example:

```
Estás hablando con {{name}}
```

### Custom Design Mode

**Custom Design Mode** is a feature that allows you to customize the appearance of the SmartUp Agent, light and dark mode, using SmartUp Interoperability features.

### Custom CSS

**Custom CSS** is a feature that allows you to customize the appearance of the SmartUp Agent component from any website, using SmartUp Interoperability features.

> 💡 If neccesary include `!important` to the CSS rule (e.g. `color: blue !important`), in order to override the default styles of the SmartUp Agent component.

HTML Elements available in the SmartUp Agent portal can be customized using CSS:

- `.agent`: Agent whole container
- `.send-message`: Send message button
- `.restart-chat`: Restart chat button
- `.message-input`: Message input
- `.agent-header`: Agent header
- `.legend-message`: Legend message (e.g. "Cargando últimos mensajes...")
- `.agent-profile-picture`: Agent profile picture
- `.message`: Message bubble

This is an example of a custom CSS to change the font and colors of the Agent component, that is also available in the [Custom CSS](https://smartup-chile.github.io/smartup-interoperability-test/custom-css/) example.

```css
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;700&display=swap');

* {
  font-family: 'IBM Plex Sans', sans-serif;
}

.send-message {
  background-color: #007bff !important;
  color: white !important;
}

.send-message,
.restart-chat {
  border-radius: 5px !important;
}

.message-input {
  border: 1px solid black !important;
  border-radius: 5px !important;
}

.agent-header {
  background-color: #007bff !important;
  color: white !important;
  border-radius: 5px !important;
  text-align: center !important;
  display: flex !important;
  justify-content: center !important;
}

.legend-message {
  display: none !important;
}

.agent-profile-picture {
  display: none !important;
}

.message {
  border-radius: 5px !important;
}
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



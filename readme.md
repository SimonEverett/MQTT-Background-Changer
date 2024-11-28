# MQTT Background Changer (HTML Only)

This project allows you to change the background color of multiple clients in real-time using the MQTT protocol. It uses an HTML page that connects to an MQTT broker and subscribes to a topic. When a color change message is published to the topic, the background color of all connected clients is updated simultaneously.

## Features
- **Real-time background color update** across all connected clients using MQTT.
- **Client-side only**: The page uses only HTML, CSS, and JavaScript, with no backend required.
- **Interactive UI**: Buttons to trigger background color changes.

## Technologies Used
- **HTML/CSS**: For the page layout and styling.
- **JavaScript (MQTT.js)**: To manage MQTT client communication and DOM manipulation.
- **Bootstrap**: For the basic layout and styling of buttons.
- **MQTT Protocol**: For lightweight messaging between clients.

## Requirements
- An **MQTT broker**: You can use a public broker like [broker.hivemq.com](http://broker.hivemq.com) or set up your own.
- A modern **web browser** to run the HTML page.

## Setup Instructions

1. **Download or Clone the Repository** to your local machine.
2. **Modify the MQTT Broker**: If you'd like to use a different MQTT broker, update the connection URL in the `<script>` section of the `index.html` file:
    ```javascript
    client = new Paho.MQTT.Client("broker.hivemq.com", 8000, "clientId-" + parseInt(Math.random() * 100, 10));
    ```
3. **Open the HTML Page**: Open `index.html` in any modern web browser (Google Chrome, Firefox, etc.).

## How It Works
1. **MQTT Client**: The page connects to an MQTT broker using the MQTT.js library. The client subscribes to the `my/test` topic.
2. **Color Change**: When a message is received on the `my/test` topic (e.g., `bg-success`, `bg-danger`, `bg-warning`), the background color of the page is updated to the corresponding Bootstrap class.
3. **Interactive UI**: The page provides buttons to change the background color. When clicked, the buttons send a message to the MQTT broker with the selected background class.

## Color Options
- **Green**: The background changes to a success green (`bg-success`).
- **Yellow**: The background changes to a warning yellow (`bg-warning`).
- **Red**: The background changes to a danger red (`bg-danger`).

## Example MQTT Message
- **Topic**: `my/test`
- **Payload**: The payload will be a string representing a Bootstrap background color class, for example:
  - `bg-success`
  - `bg-warning`
  - `bg-danger`

## Troubleshooting

- **No background change**: Make sure all clients are connected to the MQTT broker and listening for messages on the correct topic (`my/test`).
- **MQTT Connection Issue**: Check if the MQTT broker URL is correct and accessible from your network. If you're using a local broker, ensure it's running and reachable.

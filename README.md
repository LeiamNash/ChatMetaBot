<p align="center">
ChatMetaBot
    </p>
a Node.js package for creating and managing Facebook Messenger bots with ease. It provides a seamless integration with the Messenger platform, allowing developers to build dynamic and interactive chatbots effortlessly.


---

## Installation

To get started with ChatMetaBot, you need to install the package using npm:

```bash
npm install chatmetabot
```

---

## Usage

Below is a simple example of how to use **ChatMetaBot** to listen to incoming messages and respond dynamically:

```javascript
const fs = require("fs");
const login = require("chatmetabot");

login({
    appState: JSON.parse(fs.readFileSync('appstate.json', 'utf8'))
}, (err, api) => {
    if (err) return console.error(err);
    
    api.setOptions({
        listenEvents: true
    });

const stopListening = api.listenMqtt((err, event) => {
        if (err) return console.error(err);

  api.markAsRead(event.threadID, (err) => {
      if (err) console.error(err);
});

    switch (event.type) {
        case "message":
            if (event.body === '/stop') {
    api.sendMessage("goodbye", event.threadID);
        return stopListening();
    }
    api.sendMessage(event.body, event.threadID);
                break;
            case "event":
            console.log(event);
                break;
        }
    });
});
```

---

## Features

- Simple authentication with `appState.json`
- Event based message handling
- Dynamic message replies
- Supports marking messages as read
- Stop listening on command

---
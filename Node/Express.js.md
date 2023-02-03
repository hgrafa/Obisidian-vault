
## Getting Started

iniciando:

```js
const express = require('express');

const app = express();

app.listen(3333);
```

GET básico

```json
const express = require('express');

const app = express();

app.get("/", (req, res) => {
  return res.json({
    message: "Hello world ignite!"
  });
})

  
app.listen(3333);
```

Para fazer live reload enquanto o projeto estiver em desenvolvimento podemos instalar o [[Yarn#Nodemon]]

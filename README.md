# Application error reporting on google chat using google webhook API

```
Package: error-google-webhook whould be use as a middleware.
```

## Dependencies:

- **axios**
- **express**
- **dotenv**

## How to use ?

Install the package

    npm i --save express-interceptor

Configure dotenv

    WEBHOOK_URL="WEBHOOK_URL_VALUE"

```javascript
// server.js
const express = require("express");
const reporterMiddleware = require("error-google-webhook");
require("dotenv").config();

const app = express();

app.use("/", (req, res, next) => {
  res.status(502);
  const name = "Kamal";
  throw new Error("Bad Gateway Error");
});

// Use as the middleware
app.use(reporterMiddleware);

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

Run the application using

    npm start

## Limitations:

This middleware will not report for 404 and 200 responses.

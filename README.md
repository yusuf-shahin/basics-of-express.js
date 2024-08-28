# Basics of Express.js

### Introduction to HTTP :-

![Alt](https://www.course-api.com/images/slides/slide-4.png)

- [Click This Article to learn HTTP modules in details](https://www.freecodecamp.org/news/http-and-everything-you-need-to-know-about-it/)

_**HTTP-Basics**_

- http is a build module of node, it is avalavle in **node_modules** folder, so just import it in our project .
  `const http = require('http')`

**create a http server**
`const server = http.createServer((req, res) => {})`

- We pass two peremeter in _**http.createServer()**_ method **require** and **request**

![Alt](https://www.course-api.com/images/slides/slide-5.png)

**See the server in browser, listen() method. What is lesten() method?**

- listen() is an inbuilt application programming interface of the class Server within the HTTP module which is used to start the server by accepting new connections. Syntax: `server.listen(5000)` .

```js
const http = require("http");
const server = http.createServer((req, res) => {
  console.log("user hit the server");
  res.end("Hello, This is Home Page");
});

server.listen(5000);
```

**_HTTP-Headers_**

- writeHead() property, introduced in Node.js v1.0. It is part of the 'http' module. It is **used to send a response header to the incoming request.** The status code represents a _**3-digit HTTP status code**_ (e.g., 404), and the headers parameter contains the response headers.
- [What is HIIP response status code ?](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).
- `res.writeHead(200, { "content-type": "text/html" });`

```js
const server = http.createServer((req, res) => {
   res.writeHead(200, { "content-type": "text/html" });
   // res.end("<h1>home page</h1>") or -->
    res.write("<h1>home page</h1>");
    res.end();
  }
});
```

- In the server [localhost:5000](http://localhost:5000/) , any url we pass like `http://localhost:5000/about` or `http://localhost:5000/info` . The server always show us **Hello, This is Home Page**

**_HTTP-Request-Object_**

- `console.log(req.url); //# --> /`

```js
const http = require("http");

const server = http.createServer((req, res) => {
  // console.log(req.method); //# --> GET
  console.log(req.url); //# --> /

  // in url "http://localhost:5000/about/yusuf"
  // console.log(req.url); //# --> /about/yusuf

  // home page
  if (url === "/") {
    res.writeHead(200, { "content-type": "text/html" });
    res.write("<h1>home page</h1>");
    res.end();
  }

  // about page
  else if (url === "/about") {
    res.writeHead(200, { "content-type": "text/html" });
    res.write("<h1>about page</h1>");
    res.end();
  }

  // 404
  else {
    res.writeHead(404, { "content-type": "text/html" });
    res.write("<h1>page not found</h1>");
    res.end();
  }
});

server.listen(5000);
```

- to see the information from browser
- _**inspect**--->**network**-->**localhost**_

![Relative](./Image/ok-file.jpeg)

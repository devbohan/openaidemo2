node.js + Docker

## constructs

### directory

```bash
cd
mkdir docker-node-test
cd docker-node-test
```

### intall and touch

install express

```bash
npm install express
touch index.js
```

## touch index


```js:index.js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
    res.send("Hello Node.js");
});

app.listen(3000, () => {
    console.log("Start server on port 3000.");
});
```

## try node

```bash
node index.js
```

## on browser

http://localhost:3000

## add docker image

touch
- Dockerfile
- dockerignore
```bash
touch Dockerfile .dockerignore
```

### Dockerfile

base image: [bullseye-slim](https://prograshi.com/platform/docker/docker-image-tags-difference/)

```bash:Dockerfile
FROM node:18-bullseye-slim
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node","index.js"]
```

### .dockerignore

```bash:.dockerignore
node_modules
npm-debug.log
```

### build image

build image image_20230609

```bash
docker build -t image_20230609 .
```

### scoop images

```bash
docker images
```

### execute

```bash
docker run --name container_20230609 -p 3000:3000 -d image_20230609
```

### dir tree

```bash
.
├── .dockerignore
├── Dockerfile
├── index.js
├── node_modules
├── package-lock.json
└── package.json
```
refs:
[qiita](https://qiita.com/zaburo/items/bc723f9b06c8db814af3)
[jianshu](https://www.jianshu.com/p/d7401c3e8ab0)
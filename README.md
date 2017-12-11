# Ethereum Blockchain Explorer Dapp  
  
[![Blockgeeks YouTube](https://img.youtube.com/vi/Qv0tcxmApRg/0.jpg)](https://www.youtube.com/watch?v=Qv0tcxmApRg)  
  
## Install & Setup

Install ethers-cli  
```
npm install -g ethers-cli
```
**Note**: Read the [docs](https://docs.ethers.io/ethers-app/html/dev-cli.html)

Create a new project directory and initialize a project. `ethers-build init` generates a keyfile called `account.json`

```
mkdir explorer && cd explorer

ethers-build init
```

Add an `index.html` file  
```html
<html>
    <head>
        <title>Blockchain Explorer</title>
    </head>
    
    <body>
        <p>Hello world!</p>
    </body>
</html>

```

Then spin up a local webserver to serve up this html with the command
```
ethers-build serve
```

This should give us a view rendered on a localhost address, such as [http://localhost:8080/_/#!/app-link-insecure/localhost:8080/](http://localhost:8080/_/#!/app-link-insecure/localhost:8080/).
  
Add the ethers app javascript to the body and reload the page  
  
```html
<html>
    <head>
        <title>Blockchain Explorer</title>
    </head>
    
    <body>
        <p>Hello world!</p>
        
        <script src="https://cdn.ethers.io/scripts/ethers-app-v0.2.min.js"></script>
    </body>
</html>
```

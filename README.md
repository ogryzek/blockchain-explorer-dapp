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

Display the last 10 lines from the blockchain in our UI. Replace the `<p>Hello world!</p>` element with a table that defines 3 columns: Number, Hash, and Timestamp of creation. And add some inline JavaScript, using the `ethers` variable to interact with the [ethers API](https://docs.ethers.io/ethers-app/html/dev-api-blockchain.html).

```html
<html>
    <head>
        <title>Blockchain Explorer</title>
    </head>
    
    <body>
        <table>
            <tr>
                <th>Number</th>
                <th>Hash</th>
                <th>Timestamp</th>
            </tr>
        </table>
        
        <script src="https://cdn.ethers.io/scripts/ethers-app-v0.2.min.js"></script>
        <script>
            ethers.onready = function() {
                updateBlocks();
            }

            function updateBlocks() {
                var lastBlockNumber = ethers.blockchain.getBlockNumber();
                lastBlockNumber.then(function(number) {
                    console.log('The last block number: ' + number);
                    for(var i=0; i<10; i++) {
                        ethers.blockchain.getBlock(number-i).then(function(block) {
                            printBlock(block);
                        });
                    }
                });
            }

            function printBlock(block) {
                var table = document.getElementById('blocks');
                var row = table.insertRow(-1);
                var cell1 = row.insertCell(0);
                var cell2 = row.insertCell(1);
                var cell3 = row.insertCell(2);
                cell1.innerHTML = block.number;
                cell2.innerHTML = block.hash;
                cell3.innerHTML = block.timestamp;
            }
        </script>     
    </body>
</html>
```  

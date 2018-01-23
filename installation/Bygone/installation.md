# Installation Tutorial

## Requirements

Node v8: `nvm install v8`, unless using ganache-cli, see note below.

## Step 1: Get Sonar and Ganache set up

### Part 1: Clone Sonar

`git clone https://github.com/OpenMined/Sonar`

### Part 2: Prepare Sonar

We need to install the dependencies of Sonar so from the Sonar repo run the following command:

`npm install`

### Part 3: Install Ganache

Ganache is a local ethereum testing blockchain and can be using for testing and development.

It can be downloaded from here http://truffleframework.com/ganache/.

If installing for commandline you can use:

`npm install -g ganache-cli`

**Note:** If using ganache-cli use node verison 7. For example: `nvm install v7`.

You might also need to install truffle:

`npm install -g truffle`

### Part 4: Set Ganache port to 9545

Once Ganache is installed we need to set the port for 9545 so that the test suite and Bygone can find it. In Ganache, navigate to the settings in the upper right hand corner of the window and then set the port to 9545.

If running from the commandline:

`ganache-cli --port=9545`

### Part 5: Run Sonar tests

To make sure everything is working properly so far we can run the Sonar tests. From the Sonar repo run the following command:

`truffle test test/TestTrainingGrid.js`

If all the tests pass you should be good to continue!

## Step 2: Get Bygone

### Part 1: Clone Bygone

`git clone https://github.com/OpenMined/Bygone`

### Part 2: Prepare Bygone

We need to install the dependencies of Bygone so from the Bygone repo run the following command:

`npm install`

## Step 3: Configure Bygone

### Part 1: Edit config.json

The config.json should look something like below. You might not need to edit anything if the files are in the right place. I've annotated the JSON below.

```
{
  "hostname": "127.0.0.1", // ip where the server listens
  "port": 3000, // port where the server listens
  "network": "local", // local blockchain i.e. Ganache, only one supported right now
  "interface": "web3", // use web3 or uport for signing, web3 is only support right now
  "solidity" : {
    "buildDir": "build", // where to put build file
    "abiFile": "build/TrainingGrid.json", // build file name
    "solFile": "../Sonar/contracts/TrainingGrid.sol" // solidity source
  }
}
```

In the future building/deployment will probably be handled by something like truffle. But this is just how it is done right now.

### Part 2: Edit config-secret.json

Copy and paste the JSON below into a file called config-secret.json.

```
{
  "ethereumUrl": "http://127.0.0.1:9545",
  "privateKey": "PRIVATE KEY GOES HERE",
  "publicKey": "PUBLIC KEY GOES HERE"
}
```

`ethereumUrl` is the location of the blockchain to connect too. In this case it is set to where the Ganache server is running.

Fill in the `privateKey` and `publicKey` fields with the proper data. We can use the Ganache's interface for now if that's what we're connecting too. On the accounts page you can click on the key symbol next to the account. At the top there will be the public key and below is the private key. Copy and paste these into their proper fields. Make sure they both start with `0x`.

### Part 3: Run Bygone

Bygone can be starting by just running:

`node index.js`

The first time it runs and there is no `build/TrainingGrid.json` file it builds the solidity file. Next, it deploys the contract to Ganache or whatever blockchain its connected to. At this point it prints out the location of the contract:

`Deployed new contract at: 0xb9A219631Aed55eBC3D998f17C3840B7eC39C0cc`

You can copy this contract address and add it to the config file so that each time Bygone is run it doesn't need to deploy the contract. For example:

`"contractAddress" : "0xb9A219631Aed55eBC3D998f17C3840B7eC39C0cc"`

### Part 4: Connect with Unity

At this point Unity should be able to connect to Bygone and start sending experiments to it.

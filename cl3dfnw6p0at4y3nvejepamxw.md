## Using 'Thirdweb Deploy' to Launch Your Wave App Smart Contract

## Introduction

If you are reading this, I assume you have completed the [Build a Web3 app with Solidity](https://buildspace.so/p/build-solidity-web3-app) project on [buildspace](https://buildspace.so/)!

If you haven't already, enroll and complete the course to have a smart contract for this tutorial. The buildspace project is very intuitive to follow, and by the end, you will have deployed your first smart contract to the blockchain.

> Note: This guide was created for the Buildspace Women's workshop presented by Samina on May 19, 2022, and intended for educational purposes. Shoutout to [Jarrod](https://twitter.com/jarrodWattsDev) & [Raza](https://twitter.com/razacodes) for helping me put this project together.

This guide is a remix of the project and will show you how you can deploy the smart contract you created with 'thirdweb deploy' and create a frontend with thirdweb's JavaScript SDK. Also, instead of waving, we will give out some high fives instead.

## What is thirdweb?

Thirdweb is a web3 app framework that makes it easy to develop web3 apps by providing a dashboard, SDKs, and contracts to help you create web3 applications.
 
The dashboard makes it easy to deploy and manage permissions on smart-contracts. 

The framework provides SDKs in popular languages such as JavaScript, Python, Go, Unity, and C# that you can use to interact with your contracts. 

Thirdweb also offers a variety of pre-built contracts (tokens, marketplaces, treasury, and governance) to integrate into your app or import your smart contracts using thirdweb deploy.

## What is thirdweb deploy?

Thirdweb deploy is a feature that allows you to deploy your custom contracts without writing complex scripts or managing configurations such as storing keys or RPC URLs. You no longer need to worry about accidentally submitting your private keys to GitHub. 

In addition to that, thirdweb deploy allows you to add SDKs to your project and use the thirdweb dashboard to manage admin rights on the contract or view on-chain analytics. 

## Deploy WavePortal with thirdweb deploy

Before we start, I want to note that I modified the code given from the Buildspace code to remove the `payable()` functionality and the chance of winning ETH to keep the contract simple. 

Let's get started.

1. With thirdweb deploy, we don't need to worry about configuring RPC URLs or private keys in our code. Let's remove the hardhat network configuration and the dotenv line that we don't need. 

    Comment out or delete lines 7-18 in our `hardhat.config.js` file. It should look like the following:

    ```
    require("@nomiclabs/hardhat-waffle");

    module.exports = {
        solidity: "0.8.0",
    };

    ```
2. Install the thirdweb contract SDK in your repository through the terminal

    ```
    npm install @thirdweb-dev/contracts
    ```

3. Add the import statement and extend ThirdwebContract in your `WavePortal` contract. The import statement might underline in red, but don't worry about it. Your code will still compile.

    ```
    // SPDX-License-Identifier: UNLICENSED

    pragma solidity ^0.8.0;

    import "@thirdweb-dev/contracts/ThirdwebContract.sol";

    contract WavePortal is ThirdwebContract {
        // your contract 
    }
    ```
4. In your terminal run `npx thirdweb deploy` to detect, compile, and prepare the smart contract on the thirdweb dashboard. ![CleanShot 2022-05-18 at 17.29.59@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652916637649/Z_-Te8MRG.png align="left")

5. A dashboard link will open on your browser with your contract ready to be deployed. Go ahead and connect your preferred wallet that you want to deploy with. ![CleanShot 2022-05-18 at 17.37.16@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652917091253/0WDeSdJpb.png align="left")

6. Once connected, click `Deploy Now` to prepare your contract for the blockchain. ![CleanShot 2022-05-18 at 17.41.20@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652917304263/lskBvgZqC.png align="left")

7. Enter your contract's name and add an image and description. Choose the network you want to deploy on and click the blue button that says `Deploy Now.` This action will prompt you to confirm a transaction in your wallet.
![CleanShot 2022-05-18 at 17.44.03@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652917454033/7kSj2UaIx.png align="left")

8. Success! You deployed your smart contract, and now you can manage it on your thirdweb dashboard. ![CleanShot 2022-05-18 at 17.50.13@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652917857680/ASanedfHf.png align="left")

## Build our app's frontend using thirdweb's SDKs

Now that our contract's deployed, we can build out the rest of our application. To speed up my workflow, I am using thirdweb's [Next JavaScript Starter template](https://github.com/thirdweb-example/next-javascript-starter) available on GitHub.

Feel free to use vanilla JavaScript or another framework. You can install the latest version of thirdweb's JavaScript SDK in your project with `yarn add @thirdweb-dev/SDK @thirdweb-dev/react ethers`

1. Install the dependencies in the repository by running `yarn` in the terminal

2. In your `_app.js` file, change the chain to the one you deployed your contract. For this guide, I used Rinkeby.

    ```
    const activeChainId = ChainId.Rinkeby;
    ```

3. Add your newly deployed contract to your application. You can copy and paste the address directly from the thirdweb dashboard. 

    ```
    const { contract } = useContract(
        "<your-contract-address-here>"
    );
    ```
    ![CleanShot 2022-05-18 at 21.05.53@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652929588911/mZ3e3qAjY.png align="left")

4. We want to start by retrieving all the people who have waved so that we can display them on our web page. Here we will use useState and useEffect.

    ```
    const [waves, setWaves] = useState([]);

    useEffect(() => {
        async function getAllWaves() {
          const myWaves = await contract?.functions.getAllWaves();
          setWaves(myWaves);
        }

        getAllWaves();
     }, [contract]);
    ```
5. Next, we will create a button that calls our contract's `wave()` function. 

    ```
    <button
      onClick={() =>
        contract?.functions.wave("gave Samina a high five ✋")
      }
    >
      Wave
    </button>
    ```
    Notice our `contract.function.wave()` function requires you to pass it a message (string). In this guide, I am always passing "gave Samina a high five ✋" because I do not want to create an input field for text for this guide. You can choose to reconfigure this with a text input field later.

6. Lastly, I want to display all the waves I stored earlier in our code on our web app. I also added a date to keep track of the different days. 

    ```
    {waves?.map((myWaves, i) => (
      <div key={i}>
        {truncateAddress(myWaves.waver)} {myWaves.message} on{" "}
        {new Date(
          myWaves.timestamp.toNumber() * 1000
        ).toLocaleDateString()}
      </div>
    ))}
    ```
    I added a helper function to truncate the addresses and look more clean called `truncateAddress()`
    ```
    function truncateAddress(address) {
        return `${address.slice(0, 6)}...${address.slice(-4)}`;
    }
    ```

## Conclusion

That's it! 

Congratulations, you built your first smart contract, deployed it with thirdweb, and used the thirdweb JavaScript SDK to build a quick frontend.

Feel free to style your app with some CSS or add other functionalities! With code, the possibilities are endless.

As always, happy minting!
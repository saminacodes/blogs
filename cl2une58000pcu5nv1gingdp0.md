## Introduction: Build Web3 Applications With thirdweb and Next.js

## Introduction

In this series, I will teach you web3 development concepts and how to create various web3 applications using thirdweb's SDK and Next.js. We will go over web3 applications, thirdweb, how to create a crypto wallet, token, NFT, marketplace, and lastly, put it all together with a frontend.

Through the series, we will be creating a fun project that includes a custom token, NFTs, marketplaces, and a couple more features called [Cookie Project](https://cookie-project.xyz). 

Each guide will introduce concepts before we dive into writing some code. I recommend reading this series in sequence as each topic will build on top of the previous one.

## Prerequisites

This series will focus on the web3 development aspect and less on beginner web3 concepts. If you want a quick refresher on web3 concepts, check out the [Intro to Web3 Learning Path by Odyssey DAO](https://www.odysseydao.com/pathways/intro-to-web3). 

We will focus on how to build web3 applications using thirdweb's JavaScript (TypeScript) SDK. You do not need to have any experience building web3 applications to follow along. On the front end, we will be using [Next.js](https://nextjs.org), but you can also incorporate the same functionalities with vanilla JavaScript or another framework if desired.

## What is a web3 application?

The term web3 application or decentralized application refers to a web app built on a decentralized network. When we think of traditional or web2 applications, we usually have a frontend that communicates with a backend that pulls data from a database or server. The primary difference between a web2 and web3 application is the backend and database. For a web3 app, a backend is a smart contract or code that runs on a blockchain and defines your app's logic. Instead of retrieving data from a centralized database, these applications usually pull data stored on the blockchain.

If you'd like a more detailed overview of web3 architecture, I highly recommend reading [The Architecture of a Web 3.0 application by Preethi Kasireddy](https://www.preethikasireddy.com/post/the-architecture-of-a-web-3-0-application)

## What is thirdweb?

Thirdweb is a web3 app framework that makes it easy to develop web3 apps by providing a dashboard, SDKs, and contracts to help you create web3 applications. The dashboard makes it easy to deploy and manage permissions on smart contracts. It provides SDKs in popular languages such as JavaScript, Python, Go, Unity, and C# that you can use to interact with your contracts. Thirdweb also offers a variety of pre-built contracts (tokens, marketplaces, treasury, and governance) to integrate into your app or import your smart contracts using thirdweb deploy. 

#### Benefits of using thirdweb:

- **thirdweb is fully on-chain.** Thirdweb does not store any data and does not have access to your contracts which means that you don't need to trust thirdweb's infrastructure or servers. 
- **thirdweb provides SDKs in multiple popular languages and frameworks.** You don't need to learn any other web3 tool or framework. 
- **You own the smart contract you deploy.** There is no dependency on thirdweb, and you own all admin rights to the code deployed on-chain. If thirdweb disappears tomorrow, you can still access your smart contract. 
- **thirdweb's smart contracts are audited.** With the immutability nature of blockchain, it's imperative to mitigate the risk of smart-contract exploitation. With blockchain, you are often handling people's investments in large sums. You want to ensure you and any user interacting with your contract are protected.
- **thirdweb is free to use.** Thirdweb does not charge for any of the features it provides. The only fees you will be paying are transaction fees to deploy on the blockchain. 

The full suite of tools from the dashboard, SDKs, and contracts allow you to build web3 apps quickly and without much friction. In the following guides, you will learn how to use SDKs and dashboard to deploy and manage our contracts and build the frontend for your app using Next.js.

### Upcoming

Next, we will go over crypto wallets, create a crypto wallet, get test currency, and set up your development environment with your wallet.
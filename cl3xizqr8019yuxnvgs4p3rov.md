## Ch. 1: Let's Create A Crypto Wallet

## What is a crypto wallet?

To do just about anything in blockchain, you will need to create a crypto wallet. 

A crypto wallet is an application or physical device used to unlock access to your crypto assets and make transactions on a blockchain. 

Wallets have several cryptographically (fancy algorithmic math) generated components:

- **private key** - Generated hexadecimal number used to access crypto assets. This number is often compared to a password and should not be shared or visible to others.

- **public key** - Generated hexadecimal number based on the private key. A public key is similar to a username, and you can share it with others when you need them to send funds or view your transactions.

- **recovery phrase** - Secret word phrase (usually 12-24 words) used to recover a private key or import a wallet to a different wallet provider.

### Hot Wallet

A hot wallet is a wallet connected to the internet. 

There are two types of hot wallets:

- **custodial (hosted)** - With custodial wallets you do not manage your private keys. Instead, a third party, usually a cryptocurrency exchange, will manage your keys and assets for you. Some examples of custodial wallets include [Coinbase](https://www.coinbase.com/), [Binance](https://www.binance.com/en), or [Kraken](https://www.kraken.com/en-us/).
- **non-custodial (self-managed)** - With non-custodial wallets, individuals are responsible for their private keys. Some examples include [MetaMask](https://metamask.io/), [Phantom](https://phantom.app/), or [Rainbow](https://rainbow.me/).

Hot wallets are accessed from a variety of devices and browsers:

- **web-based** - Accessed from a web-browser. It does not require downloading any software.
- **mobile** - Accessed from an application downloaded to your mobile device.
- **desktop** - Accessed from an application downloaded to your desktop.

### Cold Wallet

A cold wallet is a wallet that is physical and not connected to the internet by default. This default makes them a more secure alternative to hot wallets and therefore recommended for storing large sums of cryptocurrency.

There are two types of cold wallets:

- **hardware** - Hardware wallets are a physical device that often resemble a USB stick. Some examples of hardware wallets include [Ledger](https://www.ledger.com/), [Trezor](https://trezor.io/), [Ellipial](https://www.ellipal.com/), or [KeepKey](https://keepkey.myshopify.com/).
- **paper** - Paper wallets are your private key and public key written down or printed on a piece of paper. These are generated or printed QR codes.

## Create a crypto wallet

We will need to create a crypto wallet to deploy our smart contracts to the blockchain. For development, I recommend using browser-based non-custodial crypto wallets such as [MetaMask](https://metamask.io/) or [Coinbase Wallet](https://www.coinbase.com/wallet) (not to be confused with Coinbase exchange). 

#### How to create a MetaMask wallet:

1. Navigate to https://metamask.io/download and click on Install MetaMask for Chrome (or other browser). ![CleanShot 2022-05-06 at 16.24.46@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651875897211/Awtc6IKeR.png align="left")

2. After redirecting to the chrome web store, we will install the extension. 
![CleanShot 2022-05-06 at 16.36.40@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651876625919/tuWy8e1Y8.png align="left")

3. Upon installation, we will be redirected to the MetaMask setup sequence.
![CleanShot 2022-05-06 at 16.42.41@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651876985085/3-lz9fe3Q.png align="left")

4. The next screen will prompt us to either import a wallet or create a new one. Let's go ahead and create a new wallet. 
![CleanShot 2022-05-06 at 16.44.04@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651877063290/PbcVj4sp-.png align="left")

5. MetaMask will ask if we want to share analytics to improve their services. Go ahead and confirm or decline- up to you. ![CleanShot 2022-05-31 at 10.17.14@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654013849011/wKneQu8Hy.png align="left")

6. Next, we are going to create a password. Make sure you create a super-strong password with a mix of letters, numbers, and casing. 
![CleanShot 2022-05-31 at 10.18.51@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654013984326/-lJZZoU85.png align="left")

7. After, we will receive a video that will teach us about the Secret Recovery Phrase and ways to keep it safe. Please do not skip this video. It's pretty important. ![CleanShot 2022-05-31 at 10.26.51@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654014506141/vSM3vxgHc.png align="left")

8. Go ahead and copy your recovery phrase and keep it somewhere super safe. If you lose this phrase, you will not be able to recover your wallet and any assets unlocked by the wallet. ![CleanShot 2022-05-31 at 10.33.24@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654014814670/QPcY4AWCs.png align="left")

9. Repeat the secret phrase you just copied to verify you stored it somewhere safe. 
![CleanShot 2022-05-31 at 10.38.40@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654015215484/AbTZkM2Po.png align="left")

10. Congratulations! You created your first crypto wallet. Let's go over some more practices on how to keep it safe. 
![CleanShot 2022-05-31 at 10.41.10@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654015308939/BogEZKbjW.png align="left")

## Keep your crypto wallet safe

In addition to keeping your recovery phrase safe, there are a few other practices and good hygiene you should maintain to keep your crypto wallet safe:

- Do not connect to any websites that do not have a reputation or seem suspicious.
- Disconnect your wallet from sites when not using them (we will go over how to do this in the next section).
- Be mindful to hide your private key if screen sharing. There has been instances when users have accidentally leaked it when presenting.
- Use a cold wallet to store large sums of cryptocurrency or expensive NFTs.
- Don't fall for phishing attacks. Many scammers will claim they are an official support channel to help you recover keys or provide wallet support. 
- Do not interact with any unknown assets in your wallet. 

## Upcoming
Next, we will go over some confusing parts of a crypto wallet interface and learn how to get test currency so we can start building applications.
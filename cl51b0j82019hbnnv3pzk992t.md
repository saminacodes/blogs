## How do you delete an NFT?

**Short answer:** You can't technically delete an NFT on the blockchain. Once deployed, a record of it will always exist unless the entire network goes down.

**Long answer:** Even though you can't delete an NFT, you can technically "burn" an NFT. Burning an NFT sends the NFT to a null or "burn" address. While the NFT still exists on the blockchain, it is effectively out of circulation and distribution. This method is proper when you want to reduce the supply of a token, remove spam NFTs that appeared in your wallet (be careful interacting with any unknown NFTs), or vacate an asset you accidentally created.

**Examples of burn addresses:**
- General: 0x0000000000000000000000000000000000000000 
- $SHIB: 0x000000000000000000000000000000000000dead

Looking at these addresses on Etherscan, you will notice they hold large amounts of tokens and transactions.

![CleanShot 2022-06-28 at 19.49.30@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656467388461/bBwvlaFJo.png align="left")

Unfortunately, it costs gas fees to send an NFT to a burn address because you are performing a transaction. 

Keep in mind that depending on the NFT specs, the deletion method will differ. With ERC-721 NFTs, you will be burning a specific token. In contrast, with ERC-1155, you will be burning a certain amount of those tokens. Also, note you can only delete NFTs owned by your wallet address.

### How to burn an ERC-721 NFT through EtherScan

1. Head to [Etherscan](https://etherscan.io/) and paste in the NFT contract’s address in the search bar and enter. ![CleanShot 2022-06-29 at 12.06.28@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656525998263/Oi7OXdEOx.png align="left")

    > Note: If your contract is not on the Ethereum main net, you will have to switch to the correct version of Etherscan. Click on the button with the 'b' on it to view other chains. ![CleanShot 2022-06-29 at 12.05.02@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656525922025/xP7MO4YQj.png align="left")

     You can see a history of transactions, contract balance, and other data here.

2. Navigate over to the contract tab. Here you can view the contract's code to read and write effectively. ![CleanShot 2022-06-29 at 14.09.54@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656533409587/-lNw1UonL.png align="left")

3. Click on ‘Write Contract’ to pull up a list of functions we can write to. ![CleanShot 2022-06-29 at 14.52.59@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656535998653/tk5ZxQ7Z1.png align="left")

4. Connect your wallet by clicking ‘Connect to web3’ ![CleanShot 2022-06-29 at 16.02.27@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656540161135/eTWowZhL6.png align="left")

5. Find the 'burn' function on the list and enter your token ID. Hit write, and it will prompt you to confirm a transaction. ![CleanShot 2022-06-29 at 16.18.27@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656541123099/gV46t68x2.png align="left")

6. After you burn the NFT, a button will appear with `view your transaction` where you can see the transaction that took place to burn the NFT.
    
### How to burn an ERC-1155 NFT through EtherScan

The process is very similar to the one above, except this time, you will be entering the address, token id, and the number of tokens you want to burn.

![CleanShot 2022-06-29 at 20.56.55@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656557841003/9nfN8JH-z.png align="left")

### Why burn and not transfer?

If you're curious like me, you may be wondering what the difference is between using the `burn()` function and simply transferring an asset to a burn address. Some contracts may not let you use a `transfer()` function due to convention and also preventing coins/assets from being removed from circulation. Some contracts may also take additional actions when you call the `burn()` function. 

### Conclusion

![Joker staring at burnt pile of money](https://cdn.hashnode.com/res/hashnode/image/upload/v1656609833646/wqo_oqKWB.png align="left")
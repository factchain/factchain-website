---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

## **A decentralized approach to combating online misinformation**

Misinformation on social media is a growing threat to the user experience, and centralized efforts have yet to prove helpful in flagging it efficiently. The most innovative solution so far is the **community notes feature on X** , which appeared roughly a year ago, enabling users to submit contextual notes to any post and rate other users' notes based on their **usefulness**. An open-source algorithm periodically assigns scores to notes based on their ratings. Only notes above a given score are visible to all users. [Read this excellent article by Vitalik to learn more about community notes.](https://vitalik.ca/general/2023/08/16/communitynotes.html)

X's community notes have opened the way. Still, social media posts deserve an independent and global truth layer that supports all social platforms, with immutable and transparent contributions and no central authority to trust. The protocol should incentivize users to provide notes and ratings.

This is Factchain Community.

**1 - Why become a Factchainer?**

Active factchainers are truth guardians, putting their ETH where their mouth is. The protocol rewards them when they act honestly and slashes them otherwise. More details will follow in chapter 3.

These economic incentives help secure the network, discouraging the collusion of malicious actors willing to push lousy content. Factchain Community is a fact-checking protocol, meaning there is no room for subjectivity. The protocol should prioritize notes supported by one or more external links to credible sources, convincingly demonstrating their accuracy.

Passive and active factchainers enjoy an augmented vision of their favorite social networks (X and Warpcast). More will come. They view posts with community notes and are consequently less subject to misinformation.

The protocol rewards note creators with a unique NFT tradable on Opensea and Blur. Want to collect truth fragments that contradict influential personalities? More details will follow in chapter 5. Factchain Community is an excellent opportunity to earn ETH while serving the public interest.

Make it count. Make it fun. Make it worth it.

**2 - Getting Started**

- Download the browser extension (compatible with Chrome and Brave)
- Download Metamask
- Create a Sepolia account (Factchain is only available on testnet - mainnet coming soon). You can get some test ETH [here](https://sepoliafaucet.com/).
- Visit [X](https://twitter.com/home) or [Warpcast](https://warpcast.com/).
- Connect your Sepolia account to MetaMask.
- Enjoy a refreshing social network experience enriched with community notes.

**3 - Create/Rate a Note**

A note is a text that complements a social media post identified by a URL.

A rating is a number between 1 and 5 to judge the usefulness of a note.

A factchainer can rate the same note only once and can't rate their own note.

Creating a note, like leaving a rating, triggers an Ethereum transaction to execute the relevant function from the [FactChainCommunity](https://sepolia.etherscan.io/address/0xb912368c62D3037F7E86C2e95D9B5F4FC86c9428) smart contract. These functions require a stake: 0.001 ETH (~= $20) for a note and 0.0001 ETH (~= $2) for a rating. The funds remain locked in the contract until the note auction period concludes, during which ratings are accepted.

All notes and ratings are stored forever on-chain.

The Factchain web browser extension is responsible for crafting the transactions and connecting to MetaMask for signature and broadcasting. More wallet compatibility will come.

 ⚠️ _Please exercise caution when downloading the FactChain extension to avoid potential fraudulent versions that might generate malicious transactions._ ⚠️

**4 - Rewards & Slash**

In a set period after the note creation (i.e., the note auction period), the protocol runs the scoring algorithm to assign the note its final rating. When a note surpasses the earning threshold, the protocol returns the creator's initial stake along with a reward, computed in WEI using the following [formula](https://github.com/factchain/factchain-community/blob/61eb95b29882c93344d1837d976a416ccd77ceec/fc-community-contracts/src/FactChainCommunity.sol#L113C20-L113C20). Conversely, if a note falls below the earning threshold, the protocol returns the initial stake with a slight reduction, expressed as a slash in WEI through the following [formula](https://github.com/factchain/factchain-community/blob/61eb95b29882c93344d1837d976a416ccd77ceec/fc-community-contracts/src/FactChainCommunity.sol#L120). The raters are rewarded or slashed based on how close their rating is to the final score.

**Disclaimer: For the launch on testnet, we oversimplified the scoring algorithm to an average of all note ratings, set the note auction period to 48 hours, and fixed the earning threshold arbitrarily to 3. The reward and slash logic could also evolve before the Factchain launch on mainnet. We expect to learn from users to develop the ideal strategy.**

**5 - Collect Factchain Truth Fragments**

After the note finalization phase, Factchain automatically sends an NFT to the creator, regardless of the final score. The NFT is an ERC-721 token with the following metadata pushed to IPFS:

- unique AI-generated image from the note
- attributes (note final score, social media post URL) on the [OpenSea metadata standards](https://docs.opensea.io/docs/metadata-standards).

![](assets/nft721gallery.png)

**Bonus - Mint X community notes**

To introduce Factchain to a broader audience, we have enabled the minting of every X community note as ERC-1155 tokens. Each community note is identified by its unique URL [https://twitter.com/i/birdwatch/n/](https://twitter.com/i/birdwatch/n/)\<noteID\> mapping to an NFTs collection on-chain, with a random token supply ranging from 1 to 42. Minting one or several of them does not grant any creatorship on the note but makes you one of the happy few owners of its bound Factchain NFT, with attributes described in chapter 5. (AI-generated image, OpenSea-compliant metadata)

The mint price starts at 0.0001 ETH (approximately 2.20 US dollars when writing).

---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<font size="5">
Factchain 
</font>

**Factchain** is an independent and global truth layer that supports all social platforms. It provides user contributions in an immutable and transparent way, with no central authority to trust.

Factchainers can add context to any post, in the form of **Notes** that will be rated by the community.

Useful **Notes** are shown to all users, helping them navigate real and fake news.

For their work, **Note** **Creators** and **Raters** are rewarded by the Factchain protocol, incentivising quality contributions.

[Join the faction!](https://chromewebstore.google.com/detail/factchain-community/emgjjedibkjlocjmcjgkeolfkbcicbpl)

# Get started

<li>
Download the [Factchain extension](https://chromewebstore.google.com/detail/factchain-community/emgjjedibkjlocjmcjgkeolfkbcicbpl) (compatible with Chrome, Brave, and Arc)
_Please exercise caution when downloading the Factchain extension to avoid potential fraudulent versions that might generate malicious transactions_ ⚠️
</li>
<li>
Download Metamask
</li>
<li>
Create a Sepolia account (Factchain is only available on testnet, mainnet is coming). <a href="https://sepoliafaucet.com/">Get some test ETH</a>.
</li>
<li>
Visit <a href="https://twitter.com/home">X</a> More socials will come (<a href="https://warpcast.com/">Warpcast</a>, <a href="https://www.youtube.com/">Youtube</a>...)
</li>
<li>
Connect your Sepolia account to MetaMask.
</li>
<li>
Enjoy a refreshing social network experience enriched with contextual Factchain Notes.
</li>
<br/><br/>

*TODO: show examples of what it will look like (gifs)*

# Why Factchain?

Misinformation online is the number one threat to user experience, and society at large. All content platforms have their own approach to solving the "fake news" problem, but their centralized efforts have yet to prove helpful while raising concerns about censorhip. Most existing solutions are closed source. Their decision making (human or algorithmic) is opaque and cannot be audited. As users we are asked to blindly trust that social media companies are not taking sides when it comes to content moderation, a tall ask given their less than glorious track record.

By making users the main moderators and openning up the [Community Notes](https://help.twitter.com/en/using-x/community-notes) process, Twitter/X has made a step in the right direction:
X relies on volunteers to provide context on the posts they see on their timeline by creating "Notes", and to rate the usefulness and quality of other Notes. By running these "Ratings" through a publicly reviewable algorithm, it then gets to decide which Note is or isn't worth showing to its large userbase.

While this approach is the best in the market, it falls short of the mark in a few ways:
First, if you disagree with X's algorithm, there is no way for you to propose a modified version of it that you may consider fairer.
Second, it is impossible to audit the data used by the algorithm as X ultimately controls the storing and accessing of both Notes and Ratings.
Finally, Community Notes are limited to X and they cannot be easily extended to support other platforms in their current form.

By putting Notes on-chain, Factchain goes one big step further and gives you control to make a better, more open, fact checking tool.

# How does it work?

Anyone with an Ethereum address can create and rate Factchain Notes by calling our [Factchain Contract](https://sepolia.etherscan.io/address/0x3b5946b3bd79c2b211e49c3149872f1d66223ae7).

We regularly run an algorithm to give Notes a final unified rating.

All notes and ratings are stored forever on-chain, which makes it easy for anyone to audit them and build a competing finalisation algorithm.

Creating and rating Notes requires an ETH stake. The funds remain locked in the contract until the finalisation period concludes, at which point they are distributed between all participants depending on the final rating of the Note: The better the Note, the better the rewards, but bad Notes will get you slashed. The goal is to give an incentive to users to create meaningful and useful Notes.

Notes that are deemed useful by the community are shown under their posts, providing context and nuance when navigating social media platforms.

- TODO: Quick diagram explaining the parts?

## Create/Rate a Note

A note is a text that complements a social media post identified by a URL.
A rating is a number between 1 and 5 to judge the usefulness of a note.
A factchainer can rate the same note only once and can't rate their own note.

Creating a note, like leaving a rating, triggers an Ethereum transaction to execute the relevant function from the [FactChainCommunity](https://sepolia.etherscan.io/address/0xb912368c62D3037F7E86C2e95D9B5F4FC86c9428) smart contract. These functions require a stake: 0.001 ETH (~= $20) for a note and 0.0001 ETH (~= $2) for a rating. The funds remain locked in the contract until the note auction period concludes, during which ratings are accepted.

All notes and ratings are stored forever on-chain.

The Factchain web browser extension is responsible for crafting the transactions and connecting to MetaMask for signature and broadcasting. More wallet compatibility will come.

_Please exercise caution when downloading the FactChain extension to avoid potential fraudulent versions that might generate malicious transactions_ ⚠️

## Rewards & Slash

In a set period after the note creation (i.e., the note auction period), the protocol runs the scoring algorithm to assign the note its final rating. When a note surpasses the earning threshold, the protocol returns the creator's initial stake along with a reward, computed in WEI using the following [formula](https://github.com/factchain/factchain-community/blob/61eb95b29882c93344d1837d976a416ccd77ceec/fc-community-contracts/src/FactChainCommunity.sol#L113C20-L113C20). Conversely, if a note falls below the earning threshold, the protocol returns the initial stake with a slight reduction, expressed as a slash in WEI through the following [formula](https://github.com/factchain/factchain-community/blob/61eb95b29882c93344d1837d976a416ccd77ceec/fc-community-contracts/src/FactChainCommunity.sol#L120). The raters are rewarded or slashed based on how close their rating is to the final score.

**Disclaimer $> For the launch on testnet, we oversimplified the scoring algorithm to an average of all note ratings, set the note auction period to 48 hours, and fixed the earning threshold arbitrarily to 3. The reward and slash logic could also evolve before the Factchain launch on mainnet. We expect to learn from users to develop the ideal strategy.**

## Collect Factchain Truth Fragments

After the note finalization phase, Factchain automatically sends an NFT to the creator, regardless of the final score. The NFT is an ERC-721 token with the following metadata pushed to IPFS:

<li>unique AI-generated image from the note</li>
<li>attributes (note final score, social media post URL) on the <a href="https://docs.opensea.io/docs/metadata-standards">Opensea metadata standards</a></li>

<br/><br/>
{:refdef: style="text-align: center;"}
![](assets/nft721gallery.png)
{: refdef}
<br/><br/>

## Bonus - Mint X community notes

To introduce Factchain to a broader audience, we have enabled the minting of every X community note as ERC-1155 tokens. Each community note is identified by its unique URL [https://twitter.com/i/birdwatch/n/](https://twitter.com/i/birdwatch/n/)\<noteID\> mapping to an NFTs collection on-chain, with a random token supply ranging from 1 to 42. Minting one or several of them does not grant any creatorship on the note but makes you one of the happy few owners of its bound Factchain NFT, with attributes described in chapter 5. (AI-generated image, OpenSea-compliant metadata)

The mint price starts at 0.0001 ETH (approximately 2.20 US dollars when writing).

# What's next?

*TODO: build this section*

- more socials
- more wallets + metamask snap
- better tokenomics
- mainnet

# Get in touch

*TODO: links to our socials*

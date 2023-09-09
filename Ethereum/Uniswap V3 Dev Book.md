#exchange #uniswap
[[Ethereum]]

https://uniswapv3book.com/docs/introduction/introduction-to-markets/

### Intro to markets

On centralized exchanges, the order book is where liquidity is accumulated. If someone places a sell order, they provide liquidity to the market. If someone places a buy order, they expected the market to have liquidity, otherwise, no trade is possible.

When there’s no liquidity, but markets are still interested in trades, _market makers_ come into play. A market maker is a firm or an individual who provides liquidity to markets, that is someone who has a lot of money and who buys different assets to sell them on exchanges. For this job market makers are paid by exchanges. **Market makers make money on providing liquidity to exchanges**.

### What is an AMM? [#](https://uniswapv3book.com/docs/introduction/introduction-to-markets/#what-is-an-amm)

An #AMM is a set of smart contracts that define how liquidity is managed. Each trading pair (e.g. ETH/USDC) is a separate contract that stores both ETH and USDC and that’s programmed to mediate trades: exchanging ETH for USDC and vice versa.

The core idea is **pooling**: each contract is a _pool_ that stores liquidity let’s different users (including other smart contract) to trade in a permissioned way. There are two roles, _liquidity providers_ and traders, and these roles interact with each other through pools of liquidity, and the way they can interact with pools is programmed and immutable.

![Automated Market Maker simplified](https://uniswapv3book.com/images/milestone_0/amm_simplified.png)

What makes this approach different from centralized exchanges is that **the smart contracts are fully automated and not managed by anyone**. There are no managers, admins, privileged users, etc. There are only liquidity providers and traders (they can be the same people), and all the algorithms are programmed, immutable, and public.
---
title: Quadriga loses a ton of ETH due to bad contract
date: '2017-06-02T11:10:12+00:00'
datetime: '2017-06-02T15:10:13.772Z'
---
Quadriga got 60,000 of their ETH locked up in a buggy contract:

> Earlier this week, we noticed an irregularity with regards to the sweeping process of incoming Ether to the exchange. The usual process involved sweeping the ether into a ETH/ETC splitter contract, before forwarding the ether to our hot wallet. Due to an issue when we upgraded from Geth 1.5.3 to 1.5.9, this contract failed to execute the hot wallet transfer for a few days in May. As a result, a significant sum of Ether has effectively been trapped in the splitter contract. The issue that caused this situation has since been resolved.

> Technical Explanation

> In order to call a function in an Ethereum contract, we need to work out its signature. For that we take the HEX form of the function name and feed it to Web3 SHA3. The Web3 SHA3 implementation requires the Hex value to be prefixed with 0x - optional until Geth 1.5.6.

> Our code didn't prefix the Hex string with 0x and when we upgraded Geth from 1.5.3 to 1.5.9 on the 24th of May, the SHA3 function call failed and our sweeper process then called the contract with an invalid data payload resulting in the ETH becoming trapped.

> As far as recoverability is concerned, EIP 156 (https://github.com/ethereum/EIPs/issues/156) could be amended to cover the situation where a contract holds funds and has no ability to move them.

> Impact

> While this issue poses a setback to QuadrigaCX, and has unfortunately eaten into our profits substantially, it will have no impact on account funding or withdrawals and will have no impact on the day to day operation of the exchange.

> All withdrawals, including Ether, are being processed as per usual and client balances are unaffected.

_________________________________

[Redditor comments](https://www.reddit.com/r/BitcoinMarkets/comments/6es45d/daily_discussion_friday_june_02_2017/did5d0q/?utm_content=permalink&utm_medium=front&utm_source=reddit&utm_name=BitcoinMarkets): "I wrote a buggy eth contract and now my funds are lost" will become as common on the eth sub as "I sent bitcoin with low fee and now my tx is stuck" is on the bitcoin sub.
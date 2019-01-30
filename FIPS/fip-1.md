# Introduction
Fantom is a new distributed ledger that is a secure, fast, decentralised, and permissionless network, allowing anyone to transact or build applications on top of it.

In order to secure the network, Fantom has chosen to employ a "Proof of Stake" token model, borrowing from some of the best ideas out there in the team's opinion.

There will be two types of nodes on the network: validator and listening nodes.

**Validator nodes** actively participate in the consensus of the network to validate transactions. A supermajority (⅔) of the total validating power of the network is needed to confirm a transaction to finality. These nodes will require a minimum stake.

**Listening nodes** connect to other nodes in the network and synchronize the entire ledger. They can submit transactions to the network independent of other nodes. However, they do not participate in consensus, and no staking is required.

The total validating power of the network is the total number of votes an event block can receive in the network, of which a minimum ⅔ is required to achieve finality. Note that an event block that contains no transactions can still be validated by the network, and a block reward will be earned, but no transactions fees.

# Deliverable

The deliverable of Fantom's Proof of Stake model is to:

1. Encourage stakeholders to participate in network validation via attractive and sustainable rewards for staking

2. Achieve predictable transaction and storage costs

3. Create a positive feedback loop to encourage the growth in the network. As demand for the network grows, returns for validators should also grow, which in turn should increase the demand for FTM.

# Key Features for Network Users

Users on the network will be able to use their tokens in two ways:

**Transaction-based staking**: Any participant of the network, including a wallet user, can stake a percentage of tokens to gain a percentage of guaranteed transaction volume on the network

**Paying for transactions**: Like Ethereum or Bitcoin, users will be able to pay per transaction to be confirmed by the network

## Transaction-based Staking

Owning a percentage of staked FTM tokens will guarantee a percentage of nominal network processing capacity at all times. Given a user's FTM holding, there will be a guaranteed amount of gas a user can spend per block. This is also known as "transaction-based staking".

It is extremely unlikely that all FTM holders will constantly use all of their allotted capacity. In addition, actual network capacity is likely to exceed nominal capacity. It is therefore likely that significant free capacity will be available in most blocks. That free capacity will be available to users in proportion to their staked weight. This will allow users who do not own many tokens, but are active in the system, to have preferred access to processing capacity.

FTM has a maximum supply of 3.175 billion tokens, of which **more than 30% are available for block rewards on mainnet launch**. The foundation has been actively purchasing FTM on the market over time in order to increase our block rewards, essentially removing it from total circulating supply.

## Predictable transaction and storage costs

Transaction costs will be expressed in terms of an internal accounting system called Fantom Gas ("FTG").

FTG will operate in a similar manner to gas on the Ethereum network at a virtual machine level. There will be a cost associated with each op code executed by the register-based virtual machine (costs will be specified in future technical documents. For now Fantom will follow the Ethereum Virtual Machine (EVM) gas costs as specified in "Appendix G. Fee Schedule" of the Ethereum "Yellow Paper" as Fantom is currently using Golang and Rust Implementations of the EVM). The relationship between FTM and FTG is similar to the relationship between Wei and Gas in Ethereum:

FTM = FTG_price*FTG

Where:

**FTM**: Fantom Token

**FTG**: Fantom Gas

**FTG_price**: The price of FTG in terms of FTM. This will be discussed below.
Fantom aims to achieve predictable transaction and storage costs to give users certainly over the cost of running services on the network. With networks such as Ethereum, the cost per transaction in terms of Wei can vary greatly according to the gas price.

As such, Fantom proposes the creation of a Special Purpose Vehicle ("SPV") with a built-in exchange for FTG in the network. Users will be able to buy FTG to pay for computation in advance.

FTG represents a fixed amount of processing capacity.

FTG can be bought only with FTM, via an internal exchange.

There will be an internal price "oracle" for the FTG/FTM exchange rate. FTM holders will vote on the exchange rate.

A reserve pool (SPV) will be built (holding x amount of FTM) so that there will be liquidity for the exchange.

The reserve pool will also serve to guarantee a minimum block fee during periods when transactions do not cover validator costs (more details to be added).

Any user can buy FTG using FTM using the prevailing exchange rate. From the user's perspective: FTM debit, FTG credit. The opposite will be true for the SPV.

Users can also convert FTG back to FTM via the exchange, subject to a 10% fee. From the user's perspective: FTM credit, FTG debit. The opposite will be true for the SPV.

FTG hoarding will be discouraged in a natural way: as FTG roughly follows some cloud computing/storage index, its value will slowly decline versus fiat over time, given the historical decline in both computing and storage costs. This will be a natural disincentive to hoarding.

### How are fees paid?

If a user holds FTG, this will be used for tx fees. User: FTG debit. SPV: FTG credit, FTM debit. Validators: FTM credit.

If a user does not have FTG, FTM will be used directly at prevailing rate. User: FTM debit. SPV: FTM credit. Validators: FTM credit.

However, there are several open issues to confirm. The fee split between the SPV and validators is crucial. Part of the SPV income will be a share of transaction fees, as well as on the spread of users selling back FTG to FTM.

However, the SPV will need to guarantee minimum validator income. An additional risk is the price volatility in the FTM/FTG price. Consider the following scenario:

Assume 1 FTM = 3 FTG.

A user buys 30 FTG for 10 FTM.

FTM crashes in terms of FTG, and now 1 FTM = 1 FTG.

The user sells 30 FTG back to the exchange for 27 FTM (30 less 10%)

Result: a net gain of 17 FTM for the user, a net loss of 17 FTM for the SPV
To remove this risk, we set a rule that a user can never make a profit from converting back FTG to FTM. This will be discussed in further detail.

The SPV could accumulate FTM over time. Users of the network can participate in on-chain governance (We will discuss this in more detail in future posts), as to what the FTM will be used for. For example, users may vote to burn FTM, or choose to distribute it to validators as additional staking rewards. We believe that this should drive demand for FTM, as validating becomes more attractive.

## Organic growth of network capacity according to demand

Fantom predicts that network capacity will grow in line with transaction volume. As a result, the same percentage of FTM tokens held should, over time, give access to a larger processing capacity.

# Incentives for active users

The weight given to users in the system will depend on two factors:

1. Their staked FTM holdings, and
2. The measure of **activity** over the past 6 months, with more recent activity weighted more heavily.

Activity is defined based on the amount of gas spent over time in the transactions submitted by the node to the network. There will be a minimum amount gas required to be spent per node in order to receive rewards. This should incentivise nodes to use the network. This is known as **Proof of Importance**, an idea that has been expressed in other platforms such as NEO.
We will develop a suitable formula which will combine these two factors.

# Key features for developers

##Dapp-based staking

One of the issues with the current Ethereum Proof of Work model is that developers are not incentivised to create and run Dapps on the network. Instead, Ethereum has been used to largely to conduct Initial Coin Offerings to fund projects in competition to the network.

In order to incentivise the growth and development of Dapps on Fantom. We propose a concept called **Dapp-based staking**. A developer who deploys a Dapp can stake a certain number of FTM to the network, and users will be able to use the application for free according to the rules set by the developer.

This will be feature of smart contracts on the Fantom network, where a developer can pay in FTM into the contract account to allow free use of the app as long as there are FTM left. The contract account has a FTG balance, fees are first taken from this balance, and only secondary taken from the user. This way as long as there are funds remaining the dapp is free. If the owner leaves, users can still fund the contract itself.

# Network validators

##Number of validators

In order to ensure a fast network, and also to limit costs, the system will favour the emergence of a reasonable number (50) of high-performance nodes as validators to begin with. The number of validators may grow over time depending on how many users decide to stake (given Fantom will be a permission-less network).

Node performance is defined as:

1. Processing capacity per second, which can be measured for example by the maximum number of simple transactions per second, and

2. Networking Throughput

*Note: 50 nodes is a starting point so the network can scale safely and properly so users can monitor the network and make sure it is secure as the network grows.*

## Token staking
In the single-shard model, a validator must stake at least 0.2% of the total FTM supply (6,350,000 FTM) of their own tokens. This number, as well as many other network settings, will be subject to change via on-chain voting. They will also change when Sharding is introduced.

##Block Rewards for Validators (Fees)

In return for staking FTM, attesting to correct blocks, signing off on the validity of a block, and proposing blocks, validators will be rewarded in at least two ways:

1. A fixed amount to compensate for the cost of running a node, to ensure that validators do not run nodes at a loss

2. A portion of network transaction fees. This is determined by the total number of transaction fees generated by all transactions in event blocks.

Because transaction prices will essentially be fixed, the key way for validators to increase income is by increasing processing capacity.
Here is a way that would allow users themselves to signal the need for higher transaction capacity. Suppose a user has the choice between staking tokens for transacting and staking tokens for validation (ignoring Dapp-based staking).
When there is plenty of processing capacity, we would expect more of validation staking. But as demand for transactions grow, we could see a shift towards transaction staking. As transaction staking volume exceeds a certain level, this would trigger an increase of the baseline processing limit (equivalent to a block gas limit), which would become effective only when a large majority of nodes prove they have the necessary capacity. The advantage is that this would provide a clear and **visible** signal to the entire network to increase processing capacity. This might happen even before actual volume increases, as users increase their transaction staking in anticipation of increased future transaction volume (increased buying of FTG could also provide such a signal). Note that this will require a way to occasionally measure validator processing power.

##Network security

**Penalties**: validators will have a significant amount of FTM token staked, which will be at risk if malicious behaviour is identified. Penalties are necessary in a Proof of Stake system in order to disincentivize bad behaviour and avoid the **nothing-at-stake** problem, where, absent any penalties, a validator is incentivise to bet on every possible fork of the network, as there is no lost for doing so.

In the Fantom network, we propose three types of penalties:

1. **Demurrage Fee**: A wallet will need to submit a minimum number of transactions over a given period of time or pay a certain fee. This should encourage network activity. The fee is paid proportionally to validators on the network.

2. **Validating rejected event blocks**: Nodes will need to stake for each event block they want to earn fees off of. If an event block is not ultimately not confirmed by ⅔ of the total voting power of the network, then the stake is lost, and distributed proportionally to other nodes.

3. **Network pruning**: Potentially malicious nodes will be quickly eliminated. Slow nodes will be identified and their rating down-voted, making them less likely to be selected for validation.

# Future Developments

The team is focused on analyzing key numbers for the concepts listed above, as well as making several improvements.

The numbers the team will be working on include:

1. Formula for calculating staking returns, which is currently a combination of staking amounts and Proof of Importance
2. Percentage of guaranteed transactions in return for a percentage of staked FTM
3. Percentage of guaranteed transactions when staking for a Dapp
4. Block rewards
5. Minimum staking requirements for a validating node
6. Minimum gas / transaction requirements to gain a Proof of Importance Score
7. Quantifying node performance
8. Maximum number of validating nodes before performance degradation occurs
Penalties:

1. Demurrage Fee
2. Network Pruning

# Other ideas Fantom is currently exploring

In addition to the concepts listed above, Fantom is also exploring the following:

1. **Multiple Fantom mainnet chains** employing different variations of the "Proof of Stake" model with different parameters, connected through Digital Rights Control Management (DRCM). Given that there is a level of unpredictability in how people will actually behave on the network, users might be able to choose from many chains, and the best will be chosen over time.
2. **Transaction mining solutions**: Transactions themselves are rewarded. Consequently, nodes are incentivised to a) create transactions and b) validate transactions.
3. **Paying for storage**: Over time, the network is likely to contain data that becomes unused. For example, Dapps can be abandoned for a variety of reasons. On centralised servers such as AWS, a developer must continue paying for storage costs per byte. However, on networks such as Bitcoin or Ethereum, storage is paid once and stored in perpetuity for free. This leads to the following problems:

* The network becomes increasingly bloated with unused data.
* Users have to maintain this unused data to maintain state.

We are actively working on incorporating a "rent-based" model into the Fantom network. Further details about this problem can be seen here.

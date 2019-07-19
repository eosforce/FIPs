# EOSFORCE Mainnet Improvement Proposal FIP#7

Proposer: Jeepool Jiuzhouziben Corce team

`EOSFORCE.IO` an EOSIO-based blockchain with different governance concepts, has been running stably for one year.
`EOSFORCE.IO`’s governance has been gradually recognized by the community in practice.
As the world's first large-scale network of practice in Staking Economy, EOSFORCE.IO was the first to encounter some system models and community governance related issues.
This proposal will propose improvements based on current network operations and community governance for community discussion and block producer’s parliament voting.

## Concept definition

- BP: It indicates the block producer, or the super node. It’s one of the top 23 nodes based on the weighted votes ranking.
- Profitable node: A registered node that can obtain the rewards of voting.
- Current voting: There is no fixed period for users to participate in voting.
- Fix-time voting: Users choose to vote in different voting time periods.
- Weighted votes: The number of votes calculated according to different weights of the current voting and fix-time voting

> Remarks: Time periods presented in this proposal are the corresponding block heights on the chain. For ease of understanding, the time periods are used in this proposal.

## 1. Adjust the inflation rate

It is recommended to adjust the inflation rate. The additional issue amount is 20% of the total amount of the previous year's token.

## 2. Adjust the voting weight-to endue long-term investors on the chain with more voting right

Users participating in EOSFORCE mainnet voting can choose the current voting and the fix-time voting.

**Fix-time voting**:

Users can select different voting periods to vote. The time periods are the block heights corresponding to 3 months, 6 months, 12 months and 24 months respectively. The tokens are locked during the fix-time voting period and automatically unlocked when it expires.

3 months, 6 months, 12 months, 24 months correspond to different weights of 1, 2, 4 and 8 months respectively. Rewards of fix-time voting can be received at any time. The weight of the votes will be zero clearing after the votes expire.

**Current voting**:

Users can vote without fixed period, and the voting tokens can be redeemed at any time. The redemption needs 3 days to unlock the block height. 
Weight of current voting is 0.2.

Remarks:

- 1.Rewards of fix-time voting can be received and re-invested at any time, but the principal cannot be released before the end of the fix-time period.
- 2.Fix-time voting and current voting can switch nodes at any time, just paying the fees of the system itself.
- 3.The redemption of current and fix-time voting still requires a 72-hour block height redemption period.
- 4.If this proposal is implemented, a transition period is required for the redemption of the vote. It is recommended it takes effect after the upgrade being implemented 3 days later.

## 3. Reward and punishment mechanism of nodes’ block-generating-to encourage nodes to maintain the long-term stability of the network

### 3.1 Node rewards

The EOSFORCE mainnet nodes are divided into BP nodes and profitable nodes. In order to make it more friendly to participate in the governance, the node rewards are adjusted as follows:

- 10% of block rewards is distributed by the block-generating nodes in proportion to the number of blocks.
- 10% of block rewards is distributed by all profitable nodes’ rewards according to the proportion of voting weighted votes.
- For 50% of block rewards, the nodes can freely adjust the dividend ratio.
- 30% of block rewards goes to decentralized budget system.

### 3.2 BP Reward

The reward of block producers is 10% of block rewards, which is distributed according to the weight of block-generating age(the continuous time of block-generating).

### 3.3 BP Stability

Initial value is 0. 1 will be added with no block missing within each cycle of 699 blocks. Maximum is 3800. There will be no value added if it reaches 3800. Once there is block missing, the value will be reset to 0.

Here we suppose:

In period $C_j$, reward of Block $j$ is $R_j$, block-generating amount is $N_j$,

Suppose:

- Weight set of BP stability:  $U=[U_1,U_2, ... , U_n]$
- Block-generating set of BP: $O=[O_1,O_2, ... , O_n]$

So:

- For single BP, block-generating hash rate is :$P_j$ = $O_j$ * ($U_j$+1000)
- Total block-generating hash rate on the chain is:  $P_{sum}$ = $∑_{k∈n}R_k$
- Total block-generating reward is: $R_{sum}$ = $R_j$ * $N_j$ * 5%
- Block-generating reward of single BP is: $R_n$ = $R_{sum}$ * $P_n$ / $P_{sum}$

Stability is related to the weight of BP rewards. The weight will be higher if blocking-generating is persistent and stable. In the case of generating same blocks, the higher stability the more node rewards.

### 3.4 Reward Receiving

The rewards of block-generating and voting fee can be received when the rewards are at least 100 EOSCs. The minimum receiving duration is 28800 block heights.

> Remarks: In order to make it more friendly to participate in the governance,
> block-generating rewards and voting fee rewards belong to 2 different reward pools, which need to be received separately.

### 3.5 BP Deposit

Block-generating node needs to provide a part of tokens as a deposit. If the deposit is under the minimum amount (which is coin-generating amount*700*2 of each block), there will be no block-generating reward, and the node won’t be allowed to join the election of BP.

If the deposit is deducted to a minus when generating blocks and no supplement is offered, the reward will be cancelled. All users voted to this node won’t get reward, and the node won’t have income.

> Remarks:The minimum of node deposit is the block-generating rewards of 24 hours,
> which is the time for the community to make a resolution for nodes which don’t generate blocks.

### 3.6 Block Missing Punishment

The deposit will be deducted for the block missing of the block-generating node, and twice the deposit of the reward of the block will be deducted for each less produced block.
If the node continuously miss more than 9 blocks, anyone can propose the multi-sig punishment to kick the node out.
The penalty will be divided by the user who proposed the multi-sig punishment and top 16 block-generating nodes which agree with the multi-sig punishment (20% for proposer and 80% for 16 nodes). A deposit of 100 EOSC is needed for the proposal of multi-sig punishment. After 14400 block heights, the deposited token can be returned whether the proposal is adopted or not.

The kicked-out node will be put under an observation period of 1 hour, during which user voting has no mining reward, and nodes don’t have any reward neither. After the observation period, BP can apply for a normal status to participate in the normal election and make normal mining profits.

> Remarks:The penalty goes to penalty pool first. If the multi-sig proposal is not adopted, the penalty will accumulate.
> If the proposal is adopted successfully, the accumulated penalty of the node will be distributed.

## 4. Establish a decentralized budget system- to support ecological development

- By establishing a decentralized budget system on the chain, anyone can initiate a budget proposal. 30% of the inflation issue goes into the budget system and does not impose a total amount limit. The decentralized budget system has separate account permissions, and account permissions are owned by the system. The approval authority is owned by the management committee.

- The sponsor needs to pledge 100 EOSC as deposit for the proposal to prevent bad proposals. The deposit will be returned after the proposal is passed.

- The proposer needs to specify the objectives of the proposal, the implementation details (cycle, cost, amount) and the return that the proposal will bring.

- After the proposal is approved by the management committee, there will be a 7-day publicity period. If more than one-third of the profitable nodes are opposed during the publicity period, the proposal can be rejected. If the proposal is not rejected during the publicity period, the system will automatically issue the award to the applicant's account on a monthly basis after the publicity period. During the award payment period, the management committee and the profitable nodes are greater than one-third of the veto, and the proposal award can be suspended.

- 4.5 After the proposal has passed the publicity period, the proposer will get the EOSC tokens applied for in the next block award to implement the proposal content.

## 5.	Establish the EOSFORCE Mainnet Management Committee mechanism : a more professional and effective decentralized organization to encourage the development of the chain

The EOSFORCE network management committee is designed to manage and approve proposals for a decentralized budget system, monitor the implementation of the sponsors, and promote a more equitable distribution of the decentralized budget system. Hereinafter referred to as the management committee.

- The initial membership of the management committee shall be 5 seats, followed by 2 seats every six months with a maximum of no more than 23 members.
- Any individual or organization may run for membership of the management committee. The governing council is made up of the top 5 BPs according to the votes.
- The management committee has the right to review and approve the decentralized budget system, but does not have the ownership. The ownership is owned by the system.

Remarks:

- Each management committee is tenable for half a year, and each one can take up office for 2 years continuously.
- All proposals need the approval of more than two-thirds of the management committee to become effective.
- The management committee shall set up an impeachment mechanism. Anyone who initiates impeachment can initiate impeachment, and any member who passes the vote of more than 1/3 profitable node can be impeached.
- Election criteria for the management committee are set by the block producers.
- 5% of all the adopted proposal fee is automatically paid into the account of management committee as the salary for the membership.
The above is only a proposed scheme, and the final result is still to be determined by the EOSFORCE mainnet block producers parliamentary voting.


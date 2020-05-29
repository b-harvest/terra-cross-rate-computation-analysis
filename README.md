**Github Issue**

[https://github.com/terra-project/core/issues/342](https://github.com/terra-project/core/issues/342)


**Related Analysis**

[https://medium.com/@contact_91159/terra-sdr-arbitrage-and-cross-rate-calculation-a77bfee70ca0](https://medium.com/@contact_91159/terra-sdr-arbitrage-and-cross-rate-calculation-a77bfee70ca0)

**Describe the bug**

The state machine computes cross-exchange-rate from votes as below

1. calculate median price for each Luna/Terra rates voted
2. use the calculated median prices to calculate cross-rate

**Problems**

The current calculation mechanism does not accurately capture the cross-rateCurrently it is creating highly volatile cross-rate, resulting in creating very frequentcross-rate swap arbitrage opportunity which drains the network's asset

**Suggested Solution**

The state machine should be

1. first calculate each implied cross-rate from each validator's votes
2. derive the median of implied cross rates of each validator
3. if one of the Luna/Terra rate is unavailable for a validator's votes, it is neglected during computation of median

**Contribution Work Contents**

1. Complete codebase and document Pull Request on Github
2. A test code to check the functionality of new cross-rate computation process
3. A broad risk analysis report on instability of cross-rate oracle prices

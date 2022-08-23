# Distributed Computing Environment with Rewards
## Economic Influences

Imagine a rewards-based distributed computing environment where actors
are semi-trustworthy. They will preform the computation correctly if incentivized,
but they will not perform the computation if they can get a reward 
without it.

If only one Actor is asked to perform the computation then that Actor
will be incentivized not to perform the computation and instead return
invalid results.

### Two Actors

If two actors must both complete the computation to receive the
reward then there will be an incentive for one actor to perform
the computation and while the other actor shirks responsibility 
to perform the computation and both Actors share in the rewards.

If two actors must both complete the computation to receive
a reward but do not know they are working for the same reward,
then they each will complete the computation if they know there 
are others working on the computation. 

### Actors shirk computation

If two actors know that each is working on a computation
they can agree that only one will perform the computation 
and the other will not. They will both share in the reward.

A guaranteed way to prevent shirking computation is to make the
cost of shirking the computation greater than the cost of performing
the computation. 

Another approach would be to have a way to check the
steps of computation to ensure that each Actor performed the 
computation independently. A heavy-handed approach might be to digitally 
sign the intermediate steps. There are likely more lightweight approaches.

### Network Drops

If an Actor completes the computation but cannot communicate
the results to receive the rewards due to network partitioning.
Whether this is an issue or not depends on the network outage downtime
and timeframe required for completing the computation. If timelines
are an issue for receiving results then additional Actors can be 
employed to perform the calculations. Since this requirement is
dependent on the needs of each calculation it could be determined
dynamically for each computation along with a reward to incentivize
Actors.

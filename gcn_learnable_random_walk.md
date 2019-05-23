## Graph Neural Networks with Learnable Random Walks

For featureless graphs, the task is to learn topologies in the graph.

When each node has the same feature, (soft/hard) attention doesn't work at all, since it will start with mean pooling and there will be
no discrimination between different nodes at all.

Adding dropout on the attention coefficients works (this is equivalent to stochastically sampling), but at test time if not adding dropout
the model still doesn't do anything.

### Reverse the attention direction

Both soft and hard attention work! And soft attention works even better. Hard attention is slightly worse.

This is equivalent to learning the random walk transition probablity matrices, **sequentially**!

On the other hand, we decouple the attention mechinsm to make it two separate parts. Attend based on source node, target nodes receive, which is 
separating the procedure for directed graphs. **And it utilizes random walks intrinsically (which is more powerful, supported by working well on
featureless graphs only for finding topologies).**

#### This is worth investigating and doing more experiments for a paper.

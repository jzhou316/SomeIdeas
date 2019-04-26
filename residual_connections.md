## To Understand Residual Connections

From [Quora](https://www.quora.com/How-does-deep-residual-learning-work):

- (2016) Two recent papers have shown (1) Residual Nets being equivalent to RNN and (2) Residuals Nets acting more like ensembles across several layers.
- (2016) This essentially drives the new layer to learn something different from what the input has already encoded. The other advantage is such connections help in handling the Vanishing gradient problem  in very deep networks.
- (2017) ...because in the worst case, blocks in those “unnecessary layers” can learn to be an identity mapping and do no harm to performance.

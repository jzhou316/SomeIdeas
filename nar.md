## Depth-adaptive NAR Generation

Emit tokens at different positions from different layers. The idea is to: 1) introduce more dependency among target positions 2) further improve the efficiency by early existing.

During training, we could use deep supervision for every layer. During inference, we could use heuristics to early exit.

It can be extended to more generation tasks, other than just NAT (translation) (this is also a slightly different contribution).

Recent studies show strong evidence that this might work, and this idea is a combination of the following two works:

[1] Depth-adaptive Transformer

[2] Non-Autoregressive Translation with Layer-Wise Prediction and Deep Supervision

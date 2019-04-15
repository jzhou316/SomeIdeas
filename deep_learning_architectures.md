### Transformer

- Self attention: enables to represent a word not only based on the past, but also based on the future.
  
  For left-to-right generation, the future is masked out.
  
  For generation in other orders, unknown locations can be masked out.
  
  This is very much like **CNN**, where the locality or the neighbors of a word are defined as all the other words.
  Taking a step further, this is a special case of CNN with a **graph structure** over all the words in the sentence, where the graph is complete,
  which means that each word is connected to all the other words. In particular,
  
  - the representation of each word is a function of the representations of all the other words (actually the sum)
  - the graph, or the edge weights more precisely, is updated at every layer (by the dot products between query-key pairs)
  
  So the word (node) representations (hidden states or higher level embeddings) are updated in a two step iterative algorithm: 
  **graph convolution (neighbor aggregation)** and **soft graph update**.
 
 - Multihead attention: similar to having multiple filters in CNNs to get multiple feature maps.
   In fact, it is more similar to **grouped convolution**, with each group building a **different group** and doing convolutions **separately**, and then
   **concatenate** the results in channel dimension. Compared to directly transforming to a large channel size by a single group, doing the same
   thing multiple times with each transforming to a smaller channel size and then concatenate, the latter reduces parameters and also [prevents
   overfitting](https://blog.yani.io/filter-group-tutorial/).
   
   
### General Query-Key Mechanism

Most of the machine learning tasked can be formulated as multi-label classification tasks, whether it's image recognition, or language models
(classifying within the large size vacabulary).

The basic idea of doing this classification is to:
- have a set of representations corresponding to each class/label in the candidate set. For example, in language models, this is the output embeddings.
  In sum, in all of these tasks, this is the vectors in the last layer linear transformation before softmax.
- extract a single representation of the whole image (sentence, graph, etc.), that is most correlated with the end task
- compare the single representation with the set of label representations and make decisions (in the form of a output distribution)

Note that the label representation and the feature extraction process are trained together.

This is different from learning a different representation/feature for each each class/label, and then directly do prediction based on each feature.
The benefit would be, for example, different class might have different focus on feature extraction, i.e. the most correlated features for
different classes are better extracted from different process. And also in **hierarchical** settings, some labels are better with some kind of
features whereas other labels are better with different kind of features.

But all in all, the idea of using two vector representations for comparison by dot product is dominant in deep learning architectures. The design
should focus on:
- how to extract the feature
- how to define the label representations (this is usually just very simple)


### Linear Transformation in Deep Learning

All the deep learning models rely on linear transformation (what makes deep learning unique is the combination with non-linear functions).
Whether it's fully connected, CNN, RNN, the basic building blocks are all linear transformations with matrices.

A vector is passed to a matrix, and then a new vector is generated. The basic operation is dot product, which means in this process, the previous
vector representation is compared with a bunch of vectors in the same space, resulting in a set of scores, which are used as a newer 
representation. The model learning procedure is essentially finding these **evaluation vectors** in each weight matrix, that can help divide
the space in a way most useful to the end task. This is like **sequential decision making** based on comparisons with some "anchors" stored
in model parameters.

This is like, ask you a series of questions, and based on the sequence of your answers, information is refined, important facts can be discovered.
In a discrete case, n binary questions can divide the space into 2<sup>n</sup> subspaces. In continuous space, however, the number of 
subspaces is unlimited. **Perhaps, this is why ReLU function can help to learn** (since it always discretize the space by half), which reduces
the problem perplexity.

Thinking in this way, **the deep learning models are like a decision tree**, and the grouped convolution or multihead attention are like
many trees, which is a **random forest**. Maybe that's why it is alway beneficial to do grouped version and then concatenate for final decision.

Take a look at decision trees and forests and see if there are ideas that can borrow to design deep learning models.

  




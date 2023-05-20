In the era of LLMs, we need new evaluation dataset and metrics to assess the ability of language models.

## Dynamic Dataset

The dataset will be 3 dimensional, with x, y, and an additional time dimension.
- unsupervised dataset is one dimensional, with just x
- supervised dataset is two dimensional, with x and y
- now the dynamic dataset has the additional time dimension, t

--> we call it a **dynamic dataset**, which is different from the previous static dataset.

## New Evaluation

We want to have an evolving dataset to assess the models' knowledge about the world, with automatic pipeline to update the dataset with recent knowledge (like every months or so).

For evaluation metric, we will have a new metric about **up-to-date score** (UPD)
- this measures how much the models' knowledge is up-to-date
- imagine we have dataset versions of different times, and test the model on different times, and the distribution of the evaluation score over time can represent how much up-to-date the models' knowledge is. E.g. the skewness of the distribution
- we also want to be able to compare different models tested at different times, so probably we can have a metric that is the **equivalent knowledge date** (EKD), which is a number to represent the models' most recent date of knowledge. E.g. this could be the average of time under the evaluation score distribution
- for the up-to-date score, we also want to benchmark it against a fixed date, as the current date is a moving target. Probably we can set the target to be a past date, or a future date of like 50 years from now


We also want to have better measurement of the factuality or the knowledge the model has
- like simple QA questions, quiz type
- we also want to know the robust of the model's perception of these knowledge, maybe chaning the form of questions, or how the knowledge the model should generate


## Data Split and Testing Protocol

Good curation of the knowledge presented in the test set is important, as we do not know what data the LLMs are pre-trained on.
- We should come up with a good collection of the knowledge, that is mostly purpose-oriented, as it is impossible to avoid having overlapped with LLM training data
- Some knowledge is static (more or less), some are more dynamic (such as the senator of the house, the president, etc.)
- And different knowledge would have different cycles of changes. **This could be a good dataset analysis as well**

Publishing the test data is not a good idea, as then the LLMs can train on these knowledge and hack the scores.
- It is better to hide the test data, and pass an API for testing only, and host the scores on a website
- We can publish some development data, but it should not reveal the true distribution of the test data, to avoid ppl from hacking by training on similar datasets
- There is no need to publish training data, as we are aiming to assess the general ability of knowledge memorization of language models, not proposing a specific new task. And with the current paradigm of pre-training LLMs, specific training data is less relevant


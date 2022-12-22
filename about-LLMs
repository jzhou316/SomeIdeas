### How can we tell the model generated text is already good enough (close to human level)?

OR: How can we detect the test is generated from model or human?

After trying out ChatGPT this morning, I am impressed with its ability to generate conherent and long text.

In my case I tried to guide it to write a cover letter for a faculty position, and after a few rounds of information guidance, it generates a letter that is not so different from what I wrote!

I think the reasons are probably:
- My writing also borrows from others' writing from online, as there are many templates and there is a specific form of academic cover letter
- The model is very good at following instructions, and only make changes that I talked it to
- To to the above, the model is also good at understanding the dialogue context and make certain assumptions (for example, I didn't explicitly say "revise" but just said something is wrong, it then go ahead and revised it)

I also especially like that it leaves blank to fill in specific user information. This reduces hullcination and is more robust.

As the model generations of text are becoming better and better, how can we measure the generation quality more realibly?

For example, for the cover letter, I think it's already on par with human-level (at least with me).
- It is also because this type of document is easier and more template based
- For something more complicated, probably the bar for model reaching human-level is higher

#### Idea: design new benchmarking dataset to measure model generation quality

The dataset should consider:
- Different scenarios, composing easy and hard cases. For example, for the cover letter generation (or Wikipedia text), the model could already match human level (passing Turing test), but for novel generation or things involving logic, the model can still not surpass human
- Maybe with the general challenge: to detect machine generation from human generation, and the difficulty is graduatelly increasing for different subsets of the benchmark data

Evaluation metric:
- Classifying whether it is machine generation; if the machine generation gets detected 100% then the generation quality is bad, if it's 0% than it is perfect (passing Turing test)
  - This requires human evaluation?
  - From ChatGPT's RLHF method, I think having the model score something from the text is easier than generation the same text (thinking about the reward function in the RLHF). So we could have something similar to serve as the detection model
- (continued, another thread and more concretely) If we use a classifier trained on human text and model generation text, which model generation text to use? GPT would have better generation, other models would have weaker. Classifiers are then a moving component of this evaluation.
  - We could think about just one side: first see how human generated text look like, and then see how the machine generation fits the distribution. For example, visualizing human generations are clustered in the space, and then if a machine generation falls in the same cluster or close then we can say it's disguised in human generation which is good.

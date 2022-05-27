## extract knowledge from pre-trained models

Want to utilize the large pre-trained language models in a reliable way, with correct knowledge extraction.

#### Some hypothesis/thinking:
- From a large amount of text data used to pre-train the model, the model should have learned/memoried some facts about world knowledge.

  For example, "IPhone is a product of _", the model should output "Apple".
  "A _ is talking to my sister", the model should not output "dog/cat, etc." as the animals can not talk.
  
- The model is trained on unstructured text, which is not a sysmetic way of learning knowledge.

  How do humans know that animals cannot talk?
  - Maybe taught in school explicitly: "animals cannot talk"
  - Maybe through observations: never seen an animal talking like human
  - (even seeing animals talking, they are from a TV or a movie or a book, which we can tell the situation)

- Again the text used to train the model is unstructured, or the way of training is unstructured.

  - we humans have a world physical engine in our head, but the models do not have such knowledge/simulator of the environment
  - the data may contain text like "a dog talks to me" from a book, which the model is not able to remember the situation in a long sequence
  - the model may learn similar embeddings for "dog" and "person", and it can generate syntactically correct sentences where it can swap "dog" for "person".
  
  **-> in the generation process**, also add a layer/control for fact/knowledge/possibility checking on top of the free language generation.
  
  -> conversely, we don't need to force the model to lose the ability to do free generation: we still need the imaginatory power and compositional ability for text generation (if factuality if not a concern, or it is not in real applications)

- There might have already been works under the above framework, such as retrival from an external knowledge base/online sources for fact checking, reranking the generations, etc.

  - **one idea:** do this in pre-training, in a way that can help the model to learn the world knowledge more systematically
    - add a memory bank, as the pre-training is going on, extract knowledge in the meantime and combine the representations
    - add some structural information in pre-training, to let the model know under what situation the text is being spoken. E.g. add a label for each low level sentence, such as "real-world", "book/imaginary", to form a causal model, e.g. if the situation is "real-world", the model should never say "a dog talks to a human".
    -> the model can operate in different mode, fact telling mode, imaginary mode, like Yumi's cells
    - model structural change: the model can output some knowledge score, besides only a language score
  - **another idea:** do this in fine-tuning, to strenghen the knowledge awareness of the pre-trained model
    - the pre-trained model is a perfect tool for language formulation, but it lacks some self-checking of knowledge
    - it has learned some knowledge, but weak. We can add a fine-tuning phase to give it more explicit structure of the knowledge it has learned, and embed a module for knowledge grouding

#### Extract knowledge from pre-trained language models

We have so many large language models from different organizations (T5, GPT-3, PaLM, etc.), they all have their own properties, and we don't know/don't have a form way of knowing which one is better for what application scenarios.

They differ in data, training objectives, and other details.

Like how human follow consensus to learn knowledge (e.g. a person can learn facts from what most people say, assuming people are alreay kind of experts), we can
- treat each model as an **expert**
- get the true knowledge by **voting from the expert**




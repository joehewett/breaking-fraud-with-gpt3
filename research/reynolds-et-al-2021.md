In this note I'll discuss some lessons to be learnt from one of the papers mentioned in my Reading List - [Prompt Programming for Large Language Models:
Beyond the Few-Shot Paradigm](https://arxiv.org/pdf/2102.07350.pdf)

### 0-shot prompts can significantly outperform few-shot prompts
This paper explores techniques for "exploiting the capacity of narratives
and cultural anchors" to "encode nuanced intentions and techniques for encouraging deconstruction of a problem into components before producing a verdict"

Despite the name of the seminal paper "Language models are few-shot learners", the authors of this paper realised that in contexts such as translation, a few examples were insufficient to accurately convey the task to the model. What they posit is that it is possible to direct the model to access existing knowledge. Although prompts can be helpful in constraining the form of the output, in our there are a wide range of acceptable outputs and constraint via examples would be less beneficial than in say, language translation. 

```1-shot performed significantly worse than 0-shot. By examining the output of GPT-3 on this task we found that the decreased performance was due to semantic contamination from the 1-shot example.```

Rather than trying to infer the task from the prompts, it has been noted that the semantic meaning of the examples are interpreted as relevant to the task - the examples are considered to be part of a continuous narrative to which the generated response has to take into account. This is referred to as contamination. 

### Prompt programming 

GPT-3 has approximated the human [ground truth function](https://datascience.stackexchange.com/questions/17839/what-is-ground-truth) to a notable extent. This is evident by its  ability to not only form grammatical sentences, but also coherently employ cultural references and metaphors and model complex psychological and physical contexts.

As such, to program this model with natural language our prompt has to take into account  ```the same considerations: like the art of persuasion, it entails high-level, mentalistic concepts like tone, implication, association, meme, style,
plausibility, and ambiguity.```

Modelling how GPT-3 will react to a prompt involves modelling the average human writer. We can narrow down the task and increase our ability to reverse engineer good prompts from desired replies through the following methods. 

**Methods**
- Direst task specification - constructing the signifier

Direct task specification is a 0-shot prompt which tells the model to perform some task that it already knows how to do

A direct specification consists in constructing a signifier for the task. A signifier is a pattern which keys the intended behavior.It could be the name of the task, such as “translate”, a compound description, such as “rephrase this paragraph so that a 2nd grader can understand it"

- Task specification by memetic proxy

GPT-3 demonstrates nuanced understanding of analogies [23]. Specification by proxy is mechanistically similar to direct specification, except that the signifier keys behaviors from memespace/cultural consciousness instead of naming the behavior directly.

```
For instance, instead of specifying exact criteria for an answer to a moral question directly or using examples, you could ask Mahatma Gandhi, Ayn Rand,
or Eliezer Yudkowksy. Each will come not only with a complex biases but also assumptions about the context of the question, which would maybe take paragraphs to demonstrate or describe
```

E.g. if we want something explained simply, we may frame that task within the context of a conversation between a teacher and a student.

- Prompt programming as constraining behavior

The probability distribution produced in response to a prompt is not a distribution over ways a person would continue that prompt, it’s the distribution over the ways **any person could continue that prompt** (since the model is a function of the combined total of human linguistic output rather than that of a single person or type or person) 

As such, a culturally ambiguous prompt may generate an incoherent repsonse as if it was generated under a wide range of plausible contexts. 

As such, it is helpful to constrain the behaviour by creating a prompt not merely consistent with the desired continuation, but inconsistent with undesired continuations 

e.g. 

```
Translate French to English:
Mon corps est un transformateur de soi,
mais aussi un transformateur pour cette
cire de langage.

```

Performs pooly because of the wide array of potential ways the model interprets that it can continue this sentence. By constraining the prompt with a new line following, quotes around the text, and "Translate this French sentence into an English sentence", reliably goes up drastically. 

- Metaprompt Programming

Prompt programming requires significant human time and intuition + trial & error. This motivates automated methods to generate task-specific prompts. 

"We instead propose harnessing the language model itself via metaprompts, seeds encapsulating a more general intention that will unfold into a specific prompt when combined with additional information, such as the task question. "

"A metaprompt may be something as short as a phrase such as “This problem asks us to”, a seemingly innocuous fragment which, by prompting for a statement of the problem’s intention, sets the stage for a serial explanation of a procedure to solve the problem"


### Conclusions we can draw from this paper

- We should pursue a zero-shot setting for this use-case
- The response is highly sensitive to the prompt and the model will interpret the entire range of semantic meaning that the sentence could have. As such, prompt engineering is as sensitive to content as normal programming (in the same way a semi-colon could make the difference between 5* product and production offline)
- We can embed complex biases and assumptions into the prompt via memetic proxy, rather than trying to manually explain the context within which we want a response.
- We can constrain the behaviour of the model in our prompt through additions as subtle as quotation marks and newlines
- Metaprompt programming is worth our attention in the future if we decide that our static prompt is unable to handle the full range of AFF scenarios


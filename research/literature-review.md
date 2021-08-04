# Introduction to Prompting 

> Like programming, but more fluid. You're not programming a computer, you're writing reality. It's strange. It's always different. It's never the same twice.

>– GPT-3

## Terminology
- LM: Language model 
- Prompt: An input to an LM that triggers the LM to generate a response. The prompt can contain a small number of examples of correct answers to the task posed (few shot) or no examples (zero shot)
- GPT-3: A powerful language model created by OpenAI
- Few shot learning: Making classification or regression based on a very small number of samples. In the GPT-3 case, these are provided in the prompt given to the model.
- Zero shot: When we don't give any examples of correct answers to the question we are posing 

## What is a prompt?
A prompt is a piece of text inserted in the input examples that are given to a LM, so that the original task can be formulated as a (masked) language modeling problem. For example, say we want to classify the sentiment of the movie review "No reason to watch", we can append a prompt "It was" to the sentence, getting "No reason to watch. It was ____". It is natural to expect a higher probability from the language model to generate "terrible" than “great”. 

In our case, we're going to want to engineer prompts such tat: 
- We consistently reply to scam emails with believable responses 
- The generated responses are conducive to conversation so that we keep the scammer on the hook for an extended period of time
- The generated responses contain information relating to the content of the scam email to make the scammer think that they have a real victim 
- The generated responses steer the scammer towards revealing more information about the infrastructure of their attack, e.g. paypal addresses, secondary email addresses etc. 

## Prompt Engineering
Prompt engineering for language models evokes the designation of natural language programming. Natural language, however, is indeterministic and far more entangled and elusive in its interpretation than conventional programming languages. A successful methodology of prompt programming must import knowledge and perspectives from linguistics and communication as much as from computer science or machine learning, because **language models are the offspring of the sum of all human linguistic output**.


## Reading List

I'm going to use this mantis item to track my research into this project. 

This is a list of research I'm interested in that I'd like to centralise so that I have it at my disposal.

I'll add more fleshed out details once I've digested this research, and add some summaries and findings.

### Methods of prompt programming
- https://generative.ink/posts/methods-of-prompt-programming/

### Prompt Programming for Large Language Models: Beyond the Few-Shot Paradigm
- https://arxiv.org/pdf/2102.07350.pdf
- "Using GPT-3 as a case study, we show that 0-shot prompts can significantly outperform few-shot prompts."

### Prompting: Better Ways of Using Language Models for NLP Tasks
- https://thegradient.pub/prompting/

### Improving Language Understanding by Generative Pre-Training
- https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf
- The earliest work of using prompts in pre-trained models tracing back to GPT-1/2. 
- Authors show that by designing appropriate prompts, LMs can achieve decent zero-shot performance on tasks from sentiment classification to reading comprehension.

### Language Models are Unsupervised Multitask Learners
- https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf]
- See above

### Language Models are Few-Shot Learners
- https://arxiv.org/abs/2005.14165
- original GPT-3 paper 

### Knowledge Enhanced Contextual Word Representations
- https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf
- a comprehensive study of different prompting variants. 
- Shows that when taking prompt-based fine-tuning (instead of freezing all the parameters), the model can also achieve better performance than standard fine-tuning without prompts (but a good prompt still makes significant differences), and tuning only part of the model parameters

### Meta-prompting
- https://www.gwern.net/GPT-3-nonfiction#meta-prompts
- an introduction to meta-prompting

### Making Pre-trained Language Models Better Few-shot Learners
- https://arxiv.org/abs/2012.15723
- a suite of simple techniques combined for fine-tuning pre-trained LMs on only a small number of training examples, including
- Prompt-based fine-tuning, along with a novel method for automatic prompt generation;
- A dynamic and selective method for incorporating demonstrations in context.
- "We evaluate LM-BFF in a rigorous few-shot setting (as mentioned above) and show that LM-BFF can drastically outperform standard fine-tuning by up to 30% absolute improvement"


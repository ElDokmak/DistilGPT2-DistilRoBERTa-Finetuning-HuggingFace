# GPT2-Finetuning
First install dependinces , U have to store your authentication to [hugging face](https://huggingface.co/welcome) then input your user name and password then generate new token
(This is completly optional)
```
from huggingface_hub import notebook_login
notebook_login()
```
<div>
<img src="https://user-images.githubusercontent.com/85394315/235380254-1840bfc4-03e1-4c61-aef9-776606550c70.png">
<div>

# Fine Tunining Large Language Model
In this notebook, we'll see how to fine-tune one of the 🤗 [Transformers](https://github.com/huggingface/transformers) model on a language modeling tasks on the wikitext 2 dataset. We will cover two types of language modeling tasks which are:

### First : Causal language modeling (CLM) 
The model has to predict the next token in the sentence (so the labels are the same as the inputs shifted to the right). To make sure the model does not cheat, it gets an attention mask that will prevent it to access the tokens after token i when trying to predict the token i+1 in the sentence.
<img src="https://raw.githubusercontent.com/huggingface/notebooks/463fe54d5c4effc6fdff3836653d45fbf967f7d3/examples/images/causal_language_modeling.png">

### second : Masked language modeling (MLM) 
The model has to predict some tokens that are masked in the input. It still has access to the whole sentence, so it can use the tokens before and after the tokens masked to predict their value.
<img src="https://raw.githubusercontent.com/huggingface/notebooks/463fe54d5c4effc6fdff3836653d45fbf967f7d3/examples/images/masked_language_modeling.png">

# DistilGPT2 Model 
[DistilGPT2](https://huggingface.co/distilgpt2) is an English-language model pre-trained with the supervision of the 124 million parameter version of GPT-2. DistilGPT2, which has 82 million parameters, was developed using knowledge distillation and was designed to be a faster, lighter version of GPT-2.

# CLM Training 
**NOTE** If u are using free version of colab just like me u won't be able to complete training as it will take around 21 hours and the session will time out after just 12 hours, but when using colab pro u will finish training in about 10 hours.

But don't worry about the output cause after finishing training you will get the following : 
<img src="https://user-images.githubusercontent.com/85394315/235381575-9a3e8659-8db4-49ea-a55a-69cc2109fd6b.png">

for perplexity which is a measurement of how well a probability model predicts a sample. In the context of Natural Language Processing, perplexity is one way to evaluate language models. 
```
import math
eval_results = trainer.evaluate()
print(f"Perplexity: {math.exp(eval_results['eval_loss']):.2f}")
```
U will get perplexity of 38.17






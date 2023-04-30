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
In this notebook, we'll see how to fine-tune one of the 🤗 [Transformers](https://github.com/huggingface/transformers) model on a language modeling tasks. We will cover two types of language modeling tasks which are:

### First : Causal language modeling (CLM) 
The model has to predict the next token in the sentence (so the labels are the same as the inputs shifted to the right). To make sure the model does not cheat, it gets an attention mask that will prevent it to access the tokens after token i when trying to predict the token i+1 in the sentence.
<img src="https://raw.githubusercontent.com/huggingface/notebooks/463fe54d5c4effc6fdff3836653d45fbf967f7d3/examples/images/causal_language_modeling.png">

### second : Masked language modeling (MLM) 
The model has to predict some tokens that are masked in the input. It still has access to the whole sentence, so it can use the tokens before and after the tokens masked to predict their value.
<img src="https://raw.githubusercontent.com/huggingface/notebooks/463fe54d5c4effc6fdff3836653d45fbf967f7d3/examples/images/masked_language_modeling.png">






# DistilGPT2-DistilRoBERTa-Finetuning
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

## First : Causal language modeling (CLM) 
  ----------------------------------
The model has to predict the next token in the sentence (so the labels are the same as the inputs shifted to the right). To make sure the model does not cheat, it gets an attention mask that will prevent it to access the tokens after token i when trying to predict the token i+1 in the sentence.
  
<img src="https://raw.githubusercontent.com/huggingface/notebooks/463fe54d5c4effc6fdff3836653d45fbf967f7d3/examples/images/causal_language_modeling.png">
  
### For CLM we gonna use **DistilGPT2** 
### DistilGPT2
[DistilGPT2](https://huggingface.co/distilgpt2) (short for Distilled-GPT2) is an English-language model pre-trained with the supervision of the smallest version of Generative Pre-trained Transformer 2 (GPT-2). Like GPT-2, DistilGPT2 can be used to generate text. Users of this model card should also consider information about the design, training, and limitations of GPT-2.

## Second : Masked language modeling (MLM)
  ----------------------------------
The model has to predict some tokens that are masked in the input. It still has access to the whole sentence, so it can use the tokens before and after the tokens masked to predict their value.
  
<img src="https://raw.githubusercontent.com/huggingface/notebooks/463fe54d5c4effc6fdff3836653d45fbf967f7d3/examples/images/masked_language_modeling.png">

### For CLM we gonna use DistilRoBERTa
### DistilRoBERTa
[DistilRoBERTa](https://huggingface.co/distilroberta-base) is a distilled version of the RoBERTa-base model. It follows the same training procedure as DistilBERT. The code for the distillation process can be found here. This model is case-sensitive: it makes a difference between english and English.
  
The model has 6 layers, 768 dimension and 12 heads, totalizing 82M parameters (compared to 125M parameters for RoBERTa-base). On average DistilRoBERTa is twice as fast as Roberta-base.
  
  
  
# First : CLM Training 
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

# Second : MLM Training 
After training u will get the following values : 

<img src="https://user-images.githubusercontent.com/85394315/235544854-cb266114-0ba7-4008-8575-17ec2863c018.png">
  
for perplexity U will get :
  
Perplexity: 6.37




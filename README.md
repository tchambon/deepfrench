# Deep french

This is an implementation of the [ULMFit model](https://arxiv.org/abs/1801.06146) (Universal Language Model Fine-tuning for Text Classification) on French language.

It uses the fastai v1 library (based on pytorch). Because the fastai v1 is in development, its API can often change. This repository will be updated to take changes into account.

To install fastai v1, please follow the instructions on the official repository: [fastai v1](https://github.com/fastai/fastai).

The code is provided as jupyter notebooks.

# ULMFiT approach

The ULMFiT approach is based on transfer learning. 
The idea is to train a model that can "understand" (i.e. have an internal representation of) a language. And then to use this model to do new tasks (like classification of positives or negatives reviews).

Training the LM (language model) is a data intensive task. It requires lots of data and computation. 

But, when the LM is trained, using it to do tasks like classification is quick and requires much less data.
ULMFiT shows state of the art results with much less data and computation (using a pretrained model) than previous approaches. 

Since ULMFiT release in early 2018, other projects (using the same ideas of transfer learning with a pretrained LM) have been released with new SOTA (like Google BERT). 
ULMFiT seems to still have very competitive results and is lightweight compared to models like BERT (further testing needs to be done to evaluate the differences). 



# How the french LM has been trained

The model has been trained on a 100 million words corpus, composed of an extract of Wikipedia in french. 
You can download the pretrained weight and vocab [here](https://drive.google.com/open?id=1_0D3zv5H7iMW1qk7wHNN1yQrHi6arv8g). 

The LM has a vocabulary of 30k tokens and a perplexity of 29.3.

The model have been evaluated on the task of classifying movie reviews in two categories (positive or negatives). The movie reviews have been downloaded from a french imdb-like website and include 11K positives reviews, 11K negatives reviews as well as 51K unlabeled reviews for language model tuning.
The result is a 93% accuracy, which is good regarding other languages SOTA. 
As of today, I am not aware of a public NLP classification benchmark in French, which would be great to evaluate the model on an objective dataset.


# Deep French

Deep french is composed of:

- Weights of a pretrained LM with a perplexity of 29.3.
- Examples on how to use the model to do classification tasks.

# Planning

Available:

- Weights of the pretrained french LM ([here](https://drive.google.com/open?id=1_0D3zv5H7iMW1qk7wHNN1yQrHi6arv8g). ).
- ULMFiT classifier example notebook: how to use ULMFiT to do a classification task. The example uses movies reviews of a french website. The data have been extracted using web scrapping and are not publicly available. 
- ULMFiT LM training example notebook: how to use ULMFiT to create a new LM. This example uses wikipedia in french with an extract of 100M words for training and a validation set of 22M words. The model have a perplexity of 29.3 for a 30K vocabulary.

Next to come:

- Example on a twitter dataset for sentiment analysis. Based on the DEFT french competition of 2017, this model gives a now SOTA. 
- Implementation of a classifier using the BERT model from Google and performance comparison with ULMFiT.
- Other use cases of french LM.


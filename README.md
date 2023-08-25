# replacing-ABtest

# Replacing an A/B Test with GPT

With the growth of LLMs in recent times, I wondered how it would have an effect on experimentation process of A/B testing.

With the rapid advances in Natural Language Processing (NLP) including easy access to pre-trained models from Hugging Face and the quite impressive results coming out of OpenAI’s Large Language Models (LLMs) like GPT4, I was curious whether or not you could replace a subject line A/B test with a model built using GPT. It turns out that using GPT-3’s text embeddings, and a very simple classification model, we can create a tool that correctly predicts the winner of an A/B test 87% of the time.

## The Data 
Used the Upworthy published data in 2015, the Upworthy Research Archive which contained data for 22,666 online experiments.

<!-- Image here -->

We use itertools to get A/B testing combinations with CTR. This increases the amount of observations good enough for us to compare.

<!-- Image of combined -->

We introduce a column which gives the probability of headline A is better than B.

## The Model
We keep the model simple intentionally. The reason for the simplicity of the model is that I’m primarily interested in testing the effectiveness of language models rather than this problem specific model.

- Create text vector embedding for each headline text
- Difference between embedding are calculated by directly subtracting the embedding of headline A and headline B
- Finally, we train a classifier on this vector representing the difference and 
    make prediction about the probability that A is better than B
    
## Embedding: Bag of Words (BoW), Sentence Transformer, Distilbert and GPT3 (ada002)

- Traditional Bag-of-Words (typically not considered an “embedding”)
- The sentence transformer embeddings from Hugging Face
- The Distilbert (distilbert-base-uncased) embeddings using the Hugging Face Transformers library
- GPT3’s embeddings (ada-002) created using the OpenAI embeddings api

## Classifier: 

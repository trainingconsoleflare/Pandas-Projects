# Sentimental Analysis

### What is Sentimental Analysis ?&#x20;

**Sentiment analysis** is a field of Natural Language Processing (NLP) that focuses on identifying and extracting opinions and emotions from written text. It is used by governments and organizations to analyze large amounts of data and understand the public's opinion and emotions towards a particular topic or event.

For example, government organizations can use sentiment analysis to monitor social media and news articles to gauge public sentiment towards a particular policy or issue. This information can then be used to inform decision making and improve communication with the public.

Similarly, businesses can use sentiment analysis to track customer satisfaction and brand perception by analyzing customer reviews, feedback, and social media posts.

In both cases, sentiment analysis helps organizations to understand public opinion and make data-driven decisions to improve their policies, products, or services.

### What is AFINN ?&#x20;

AFINN is a dictionary-based sentiment analysis library developed in Python. It assigns a sentiment score to each word in a given text and then aggregates these scores to determine the overall sentiment of the text. The sentiment score can range from -5 (strongly negative) to +5 (strongly positive).

For example, consider the following sentence: "I love this product, it's amazing!" The words "love" and "amazing" have high positive sentiment scores, while the word "product" has a neutral sentiment score. AFINN would aggregate these scores to give the overall sentiment of the sentence as positive.

AFINN is a useful tool for sentiment analysis as it provides a simple and straightforward approach to determining the sentiment of text, making it a great starting point for NLP projects and sentiment analysis.

Here's an example in Python:

```python
import afinn

afinn = afinn.Afinn()
sentence = "I love this movie, it's fantastic!"
sentiment_score = afinn.score(sentence)

print("Sentiment Score:", sentiment_score)

```

**Output:**

```python
Sentiment Score: 5.0
```

AFINN library has several other features, including:

1. **Word-level sentiment analysis**: AFINN can score individual words in a sentence, not just the entire sentence as a whole.

```python
import afinn

afinn = afinn.Afinn()
sentence = "I love this movie, it's fantastic!"
sentiment_scores = afinn.scores(sentence)

print("Sentiment Scores:", sentiment_scores)

```

```python
Normalized Score: 4.5
```

**Normalization**: AFINN can normalize the sentiment score by dividing it by the number of words in the sentence.

```python
import afinn

afinn = afinn.Afinn()
sentence = "I love this movie, it's fantastic!"
normalized_score = afinn.norm_score(sentence)

print("Normalized Score:", normalized_score)

```

**Custom lexicon support**: You can provide your own lexicon of words and sentiment scores, which will be used instead of the default lexicon.

```python
import afinn

custom_lexicon = {'love': 5.0, 'fantastic': 5.0}
afinn = afinn.Afinn(lexicon=custom_lexicon)
sentence = "I love this movie, it's fantastic!"
sentiment_score = afinn.score(sentence)

print("Sentiment Score:", sentiment_score)

```

**Sentiment lexicon expansion**: You can add new words and sentiment scores to the lexicon at runtime.

```python
import afinn

afinn = afinn.Afinn()
sentence = "I love this movie, it's fantastic!"
afinn.lexicon["awesome"] = 5.0
sentiment_score = afinn.score(sentence)

print("Sentiment Score:", sentiment_score)
```

**Sentiment classification**: AFINN can classify a sentence as positive, negative, or neutral based on its sentiment score.

```python
import afinn

afinn = afinn.Afinn()
sentence = "I love this movie, it's fantastic!"
sentiment_class = afinn.classify(sentence)

print("Sentiment Class:", sentiment_class)

```

**Sentence tokenization**: AFINN can split a long text into sentences for processing.

```python
import afinn

afinn = afinn.Afinn()
text = "I love this movie, it's fantastic! I hate this book, it's terrible."
sentences = afinn.tokenize(text)

for sentence in sentences:
    sentiment_score = afinn.score(sentence)
    print("Sentence:", sentence)
    print("Sentiment Score:", sentiment_score)
    print()

```

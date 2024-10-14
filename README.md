
# Flipkart Reviews Sentiment Analysis

This project analyzes customer reviews from Flipkart to understand the sentiment of the reviews and provides visualizations such as a pie chart of ratings distribution and a word cloud of the most frequent terms in the reviews.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Data Cleaning](#data-cleaning)
- [Sentiment Analysis](#sentiment-analysis)
- [Visualizations](#visualizations)
- [Results](#results)
- [Usage](#usage)

## Introduction

This project processes customer reviews data, cleans the text, and analyzes the sentiments using Natural Language Processing (NLP) techniques. It also generates visualizations for the distribution of ratings and the most frequent words in the reviews.

## Installation

To run this project, you need the following Python libraries:

```bash
pip install pandas matplotlib nltk plotly wordcloud
```

Additionally, you need to download some NLTK resources:

```bash
import nltk
nltk.download('stopwords')
nltk.download('vader_lexicon')
```

## Data Cleaning

The data cleaning process includes:
- Converting text to lowercase.
- Removing URLs, HTML tags, punctuation, and special characters.
- Removing stopwords.
- Applying stemming to the words.

The `clean()` function handles this process:

```python
def clean(text):
    # cleaning steps
    return text
```

## Sentiment Analysis

The `SentimentIntensityAnalyzer` from NLTK's VADER module is used to analyze the sentiment of each review. Three categories of sentiment scores are generated: **Positive**, **Negative**, and **Neutral**.

```python
from nltk.sentiment.vader import SentimentIntensityAnalyzer

data['Positive'] = [sentiments.polarity_scores(i)['pos'] for i in data['Review']]
data['Negative'] = [sentiments.polarity_scores(i)['neg'] for i in data['Review']]
data['Neutral'] = [sentiments.polarity_scores(i)['neu'] for i in data['Review']]
```

## Visualizations

The project generates two visualizations:
- **Ratings Pie Chart**: Displays the distribution of review ratings.
  
```python
figure = px.pie(data, values=quantity, names=numbers, hole=0.5)
figure.show()
```

- **Word Cloud**: Displays the most frequent words from the reviews.

```python
wordcloud = WordCloud(stopwords=stopwords, background_color='white').generate(text)
plt.imshow(wordcloud, interpolation='bilinear')
plt.show()
```

## Results

The overall sentiment score is calculated based on the aggregated sentiment scores for all reviews. The function `sentiment_score(x, y, z)` determines whether the overall sentiment is **Positive**, **Negative**, or **Neutral**.

## Usage

1. **Load the Dataset**: Place the `flipkart_reviews.csv` file in the same directory as your Python script.
2. **Run the Script**: Execute the Python script to clean the data, perform sentiment analysis, and generate visualizations.
3. **View Sentiment Scores**: The sentiment scores for each review, as well as the overall sentiment, are printed.

```python
sentiment_score(x, y, z)
```

Enjoy exploring customer reviews sentiment with this project!

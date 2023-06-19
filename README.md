# 1. HOW TO RUN
#### - Installations
        - pip3 install -r requirements.txt
* Clone or download the github repository 
* Navigate to the project directory and run the ‘simple_text_analysis.ipynb’ file.

# 2. GETTING STARTED

The objective of this project is to extract textual data articles from the given URL and perform text analysis. 

For each of the articles, given in the input.xlsx file, extract the
article texts are extracted using beautifulsoup and extracted article is saved in a text file with URL_ID as its file name. (All the generated text files are given in the folder named ‘Text files’).

For each of the extracted texts from the article, textual analysis is performed to drive
sentimental opinion, sentiment scores, readability, passive words,
personal pronouns and etc.

This analysis determines whether a piece of writing is positive, negative, or neutral. The below Algorithm is designed for use in Financial Texts. It consists of the following
steps:

## 2.1 Cleaning Using Stopwords: 
The stopwords module from nltk is used to clean the text so that Sentiment Analysis can be performed by excluding the those words .
## 2.2 Creating a Dictionary of Positive and Negative Words:
The ‘positive.txt’ and ‘negative.txt’ files are used for creating a dictionary of Positive and Negative words. We add only those words in the dictionary if they are not found in the Stop Words Lists.
## 2.3 Extracting Derived Variables:
We convert the text into a list of tokens using the nltk tokenize module and use these tokens to calculate the 4 variables described below:

**2.3.1 Positive Score:** This score is calculated by assigning the value of +1 for each word if found in the Positive Dictionary and then adding up all the
values.

**2.3.2 Negative Score:** This score is calculated by assigning the value of -1 for each word
if found in the Negative Dictionary and then adding up all the
values. We multiply the score with -1 so that the score is a positive
number.

**2.3.3 Polarity Score:** This is the score that determines if a given text is positive or
negative in nature. It is calculated by using the formula:
Polarity Score = (Positive Score – Negative Score)/ ((Positive Score + Negative Score) + 0.000001)
Range is from -1 to +1

**2.3.4 Subjectivity Score:** This is the score that determines if a given text is objective or
subjective. It is calculated by using the formula:
Subjectivity Score = (Positive Score + Negative Score)/ ((Total Words after cleaning) + 0.000001)
Range is from 0 to +1

## 2.4 Analysis of Readability:
Analysis of Readability is calculated using the Gunning Fox index formula
described below.

**2.4.1 Average Sentence Length** = the number of words / the number of sentences

**2.4.2 Percentage of Complex words** = the number of complex words / the number of words

**2.4.3 Fog Index** = 0.4 * (Average Sentence Length + Percentage of Complex words)

## 2.5 Average Number of Words per Sentence:
The formula for calculating is:
Average Number of Words Per Sentence = the total number of words / the total number of sentences

## 2.6 Complex Word Count:
Complex words are words in the text that contain more than two syllables.

## 2.7 Word Count:
We count the total cleaned words present in the text by 
    1. removing the stop words (using stopwords class of nltk package).
    2. removing any punctuations like ? ! , . from the word before counting.

## 2.8 Personal Pronouns: 
To calculate Personal Pronouns mentioned in the text, we use regex to find the counts of the words - “I,” “we,” “my,” “ours,” and “us”. Special care is taken so that the country name US is not included in the list.

## 2.9 Average Word Length:
Average Word Length is calculated by the formula: Sum of the total number of characters in each word/Total number of words

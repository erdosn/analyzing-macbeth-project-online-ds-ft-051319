
# Project: Analyzing Macbeth

## Introduction
For our first day and first data science project, we're going to do some rudimentry analysis of Shakespeare's classic play: Macbeth! You will get practice working with lists, condtionals and dictionaries, visualizing data, and thinking analytically about data.

## Objectives
You will be able to:
* Show mastery of the content covered in this section

## Getting the Data
Here we start by importing a python package and using it to pull the transcript of Macbeth from the project Gutenberg website. We also preview a few details about what is now stored in the variable macbeth; it's a string with 119,846 characters, the first 500 of which are printed below. 


```python
import requests
import matplotlib.pyplot as plt
macbeth = requests.get('http://www.gutenberg.org/cache/epub/2264/pg2264.txt').text

print(type(macbeth))
print(len(macbeth))
print(macbeth[:500])
```

    <class 'str'>
    119846
    ﻿***The Project Gutenberg's Etext of Shakespeare's First Folio***
    ********************The Tragedie of Macbeth*********************
    
    This is our 3rd edition of most of these plays.  See the index.
    
    
    Copyright laws are changing all over the world, be sure to check
    the copyright laws for your country before posting these files!!
    
    Please take a look at the important information in this header.
    We encourage you to keep this file on your own disk, keeping an
    electronic path open for the nex


## Your Task

Your task is to create a bar graph of the 25 most common words in Shakespeare's Macbeth.  


A common python programming pattern to counting objects, produce histograms, or update statistics is to make calls to a dictionary as you iterate through a list. For example, given a list of words, you can create a dictionary to store counts and then iterate through the list of words, checking how many times each word has appeared using your dictionary, and updating the dictionary count now that you've seen that word again. The `dictionary.get()` method is very useful in doing this. Read the docstring for the dictionary.get() method and use it along with the pseudocode above to create a bar graph of the 25 most common words from the transcript of Macbeth which has been loaded into a variable 'Macbeth'. Be sure to include a title and appropriate labels for your graph.


```python
# Your code here

# Pseudo-code Outline
# Split the transcript into words
# Create a dictionary
# Iterate through the text of Macbeth
# Update word counts
# Create Bar Graph
# Include descriptive titles and labels
```


```python
from collections import Counter
```


```python
# Get words 
words = macbeth.split()
words[:10]
```




    ['\ufeff***The',
     'Project',
     "Gutenberg's",
     'Etext',
     'of',
     "Shakespeare's",
     'First',
     'Folio***',
     '********************The',
     'Tragedie']




```python
# create counter dictionary from words
word_counter = Counter(words)
```


```python
# create a list of tuples from the dictionary with words and counts
word_counter_tuples = sorted([(k, v) for k, v in word_counter.items()], key=lambda x:x[1], reverse=True)
word_counter_tuples[:5]
```




    [('the', 620), ('and', 427), ('of', 395), ('to', 367), ('I', 326)]




```python
# get top 25 words and turn them into a dictionary
top_25_words = dict(word_counter_tuples[:25])
top_25_words
```




    {'And': 169,
     'I': 326,
     'Macb.': 137,
     'That': 80,
     'The': 131,
     'a': 255,
     'and': 427,
     'be': 133,
     'for': 100,
     'haue': 114,
     'his': 127,
     'in': 190,
     'is': 185,
     'it': 128,
     'my': 170,
     'not': 142,
     'of': 395,
     'our': 116,
     'that': 158,
     'the': 620,
     'this': 108,
     'to': 367,
     'with': 141,
     'you': 193,
     'your': 122}




```python
plt.figure(figsize=(8, 5))
plt.grid(alpha=0.5, zorder=0)
plt.bar(range(len(top_25_words.values())), top_25_words.values(), 
        tick_label=list(top_25_words.keys()), zorder=2)

plt.xticks(rotation='vertical')
plt.title("Top 25 Words in\nMacbeth")
plt.show()
```


![png](index_files/index_9_0.png)


## Level Up (Optional)
This project should take you about an hour and a half to complete. If you're done much more quickly than that and are not behind in the course, feel free to deepen your knowledge by completing any or all of the following tasks until you run out of time:
* Create a list of top characters by mentions of their names 
* Split the text by which character is talking
* Create subgraphs of the most common words by character
* Reduce the string to the text of the play itself. (Remove any initial notes, forward, introduction, appendix, etc.)
* Come up with some other fun analyses of the text!

## Summary
Congratulations! You've got some extra practice combining various data types into useful programming patterns and done an initial analysis of a classic text!

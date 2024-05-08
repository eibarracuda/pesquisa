---
{"dg-publish":true,"permalink":"/03-acervos//2023-03-11-create-your-own-word-cloud-towards-data-science/","title":"( 2023-03-11  - 📰️ Create your own Word Cloud - Towards Data Science","tags":["🧠️/📥️/📰️/🟩️"],"created":"2024-05-08T13:44:45.293-03:00","updated":"2024-01-02T22:12:41.140-03:00"}
---


>[!abstract]+ Sobre
>- `Titulo da nota:`  [[03. Acervos/📰️/( 2023-03-11  - 📰️ Create your own Word Cloud - Towards Data Science\|( 2023-03-11  - 📰️ Create your own Word Cloud - Towards Data Science]]
>- `Tipo:`  [[(\|(]]
>- `Autor:`  Gurucharan M K
>- ` Publicado em:` 2023-03-11
>- ` URL:`  https://towardsdatascience.com/create-your-own-word-cloud-705798556574
>- `Site:` Towards Data Science - [Link](https://towardsdatascience.com/create-your-own-word-cloud-705798556574)
>- `Tema:`  Programação
>- ` Tempo de leitura:` 4
***


# [Create your own Word Cloud - Towards Data Science](https://towardsdatascience.com/create-your-own-word-cloud-705798556574)

## Learn to build a very simple word cloud using Python using only a few lines of code!

Hi everybody! Haven’t all of us seen such interesting and new forms of word clouds being displayed and wondered if we could also generate such word clouds. What if I tell you it is possible with a *Python Program* comprising of not more than ***20*** lines of code. Let’s dive in!

Image from Source ([1](https://adaringadventure.com/word-cloud-nlp/) and [2](https://algorithmia.com/algorithms/nlp/DocumentClassifier))

## Overview

In this story, I am going to show you a very *simple* and *concise* code on how to build and generate a very simple word cloud from any text data.

## Data

For generating this word cloud, I will be using a data set that was originally created for building a *spam comment classifier*.

The file `'Youtube05-Shakira.csv'` is a data set that consists of 5 columns such as the COMMENT ID, AUTHOR, DATE, CONTENT and CLASS. The ‘CONTENT’ and ‘CLASS’ columns are used to build a machine learning model to classify a message if it is a spam message or not.

For generating our word cloud, I will be using only words in the ‘CONTENT’ column.

## Step 1: Importing the Libraries

The first step in any python program will always be on *importing the libraries*. For this code we will require only *three* *libraries*, out of which two should already have been installed in your Python workspace. The only library to be additionally installed before this program is the ‘***wordcloud***’ library which can be easily installed using the ‘***pip***’ command.

\# Importing the Librariesfrom wordcloud import WordCloud, STOPWORDS  
import pandas as pd  
import matplotlib.pyplot as plt

## Step 2: Reading the Data File

In the next step, we will read the data file ( .csv file) and store in into a ***Pandas DataFrame***. The pandas data frames are always easier and faster to use when working with large datasets. The column required for our word cloud generation can be easily accessed from the pandas data frame.

\# Read 'Youtube05-Shakira.csv' filedata = pd.read\_csv(r"Youtube05-Shakira.csv", encoding ="latin-1")

## Step 3: Setting the comment and stop words

In this step, we initialize two important strings for our word cloud generation.

The ‘***comment\_words***’ is the string that will be used to store all the words of the CONTENT column in a single line of text

The ‘***stop\_words***’ is used to store all the words that are very commonly used in English language such as ‘the’, ‘a’, ‘an’, ‘in’. These words will be later filtered while generating the word cloud.

## Step 4: Iterating through the data file

Now that we have stored the data file into a pandas dataframe, we now have to convert each row of the ‘CONTENT’ column to a very long, single line of text.

The first step in this will be to ***split*** each word in a row ( a comment has a finite number of words) and store it in a variable. `separate = i.split()`

After splitting the words, for homogeneity of all the words, we convert all the words to ***lowercase*** using the `.lower()` function.

Finally, we ***join*** all the words and store it to the variable ‘comment\_words’ using the function `.join()` The variable ‘***comment\_words***’ now contains all the words in a single long text necessary to generate our word cloud.

\# Iterating through the .csv data file   
for i in data.CONTENT:   
    i = str(i)   
    separate = i.split()   
    for j in range(len(separate)):   
        separate\[j\] = separate\[j\].lower() 

          comment\_words += " ".join(separate)+" "

## Step 5: Creating the Word Cloud

In this step, we finally generate the word cloud using the ‘***WordCloud***’ function. In this we will be using the two variables ‘*stop\_words*’ and ‘*comment\_words*’. The code is self-explanatory and easy to understand.

\# Creating the Word Cloud  
final\_wordcloud = WordCloud(width = 800, height = 800,   
                background\_color ='black',   
                stopwords = stop\_words,   
                min\_font\_size = 10).generate(comment\_words)

## Step 6: Displaying the Word Cloud

The last and final step is to display our word cloud that we just generated using the above code. The ‘***matplotlib.pyplot***’ library is used to display the word cloud. Take a look at the word cloud generated below!

\# Displaying the WordCloud                      
plt.figure(figsize = (10, 10), facecolor = None)   
plt.imshow(final\_wordcloud)   
plt.axis("off")   
plt.tight\_layout(pad = 0) 

  plt.show()

Generated Word Cloud

Hurray! You have now understood how to generate a very simple and basic word cloud using Python and a few lines of code. You can now use this as a base to *generate various shapes* and types of Word Clouds!

I’m sharing a link to my github repository where the entire code in the ***.ipynb*** file is available for you to work on!

Although, this isn't a part of Machine Learning, this is one of the most basic utilization of another important field of Artificial Intelligence, the ***Natural Language Processing*** (NLP). So, go ahead and experiment with this new field of NLP. Till then, Happy Machine Learning!

***

---
title: "Disposition for Master Thesis - subdirectory"
---

# Jazz Maestro - Which Jazz Tune Should I Learn Next?

Disposition for Master Thesis MAS Data Science, ZHAW

Doris Zahnd

October 2021 - January 2022

Project Description
-------------------

Learning to play jazz can be overwhelming for a beginner. Jazz musicians rely on Lead Sheets, which only describe the basic melody and the chord structure of a tune. It is then up to the skills of the musicians to create the appropriate accompaniment, bass line and melody improvisation.

The chords are the building blocks for playing a jazz tune and it is vital for every jazz musician to know them inside out. In jazz, a chord typically consists of four or more notes, resulting in a multitude of different chord variations. In “Real Jazz Theory” \[1\], there are 40 different chord variations listed for a single root note. Considering all 12 tones of the chromatic scale, this results in 12\*40 = 480 chords to be studied.

However, many chord patterns are often repeated in the jazz tunes, or some tunes are using an identical chord structure for a part of the tune but use a different melody. When a student has learned a tune, it is therefore helpful to find a next tune to learn which is similar in chord structure, to improve the learning experience.

In the scope of this master thesis, an application shall be created that lets the musician explore the jazz tunes based on the chord progressions. The musician shall be able to select a jazz tune, and the application shall recommend tunes which are similar in chord structure.

In the capstone project for the Text Analytics module in the CAS Machine Learning, I already touched on the topic of recommending a tune using word embeddings based on chord n-grams, and found the results promising \[2\].

Goals
-----

Create an application to explore jazz tunes which has the following parts:

*   Recommender System: Based on a tune that is selected by the user, recommend another tune which is similar in its chord structure.
    
*   Explorative Selection: let the user find a tune based on multiple filter selections: default musical key, general structure of the tune (e.g. AABA), frequent chord progressions, composer.
    
*   Experimental Analysis: Analyze the Building Blocks of the Jazz Tunes, e.g. by examining how the chord progressions differ for the tunes, or if there are common patterns found per composer.
    

The front-end user interface shall be a simple web application, created e.g. with Plotly Dash.

Demarcation
-----------

The input data for this project must be in musicXML format. No audio files are used as input. No chord progressions are predicted or generated.

Though it would have been interesting, this project does not consider the melody for two reasons: I could not find an appropriately efficient way to retrieve the melodies of hundreds of tunes in musicXML or a similar digital format. Additionally, the melody is subject to the copyright of the publishing company, whereas a chord progression is not copyrightable.

Methods
-------

### Data Collection

The chord sequences, default key and composer of 1350 jazz tunes and ca. 800 traditional jazz tunes are publicly available from the iRealPro App \[3\]. They can be exported in musicXML format. Most of the tunes have section labels (e.g. AABA, ABAC, AB, ABCD….).

### Data Preparation

The musicXML files need to be transformed into a text format which can be used by the TextAnalytics algorithms. The chords need to be transposed and possibly simplified for comparison. There is code from a public github repo available \[4\] which can be used with some adaptions.

Define the data structure to store the data.

### Recommender System for Similar Tunes

Chord analysis has a strong relationship to text analysis: a chord can be considered as a word, a section as a paragraph and a tune as a document. Using Word Embedding algorithms such as word2vec for chord sequences is therefore well described in the literature, however most applications focus on generating new chord sequences based on input training data and not on the similarity of tunes. Compare TF-IDF and word2vec methods based on chord n-grams, using an appropriate metric to quantify the similarity.

The validation how to evaluate the usefulness of the recommendation is an open question and needs to be defined during the project work. 

### Analyze the Building Blocks of the Jazz Tunes

This part is experimental. Define features based on the tune structure and chord sequence and apply clustering (unsupervised), analyze the resulting clusters.

Visualize the chord progressions for a single tune or for a group of tunes using graphs.

Optional: Consider a composer who has written many tunes, and try to find whether his tunes are identifiable by using a supervised algorithm.

Time Schedule
-------------

Total effort: 12 ECTS points \* 30h = 360h → 45 days à 8h

|     |     |
| --- | --- |
| **Task** | **Effort \[days\]** |
| Data Collection & Preparation<br><br>_Data preparation, chord transformation and simplification, adapt musicXML library. Define data structure._  <br>_Note: some preparational work was already done in the scope of the TextAnalytics project of the CAS Machine Learning._ | 10  |
| Explorative Selection of Tunes<br><br>_Overview plots, define and implement selection filters in WebApp._ | 5   |
| Explore building Blocks of the tunes<br><br>_Create graphs for chord progressions. Define features, apply clustering and analyze clusters. Visualize tunes in WebApp._ | 10  |
| Recommender System for Tunes<br><br>_Compare results for TF-IDF and word2vec, explore different n-grams, select similarity measure. Visualize one resulting model in the WebApp._ | 10  |
| Documentation | 10  |

References
----------

1.  [https://www.halleonard.com/product/289283/real-jazz-theory-poster](https://www.halleonard.com/product/289283/real-jazz-theory-poster)
    
2.  [https://github.com/gruppeneun/chords/blob/master/doc/what\_should\_i\_learn\_next\_benke\_hilti\_zahnd.pptx](https://github.com/gruppeneun/chords/blob/master/doc/what_should_i_learn_next_benke_hilti_zahnd.pptx)
    
3.  [https://www.irealpro.com/](https://www.irealpro.com/)
    
4.  [https://github.com/felixxwu/Jazz-Chord-Generator](https://github.com/felixxwu/Jazz-Chord-Generator).
    

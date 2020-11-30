# Song-Lyrics-NLP
## Analysis of Taylor Swift Song Lyrics Using Natural Language Processing <br/>

### This project is split into the following parts: <br/><br/>

#### 1. Import all the necessary packages. <br/><br/>

#### 2. Obtain the lyrics from the artist, in this case Taylor Swift, by scraping them from Genius.com: 
To do so, the Python package lyricsgenius is used, which is a client for the Genius.com API. First, a Genius.com free account needs to be created in order to get an access token required to access the Genius API. <br/><br/> In this case, we search by artist and we exclude those songs which contain the terms in the excluded list. The songs will be returned and written to a JSON file with all the associated data such as album, release date, song title, etc. The file containing the downloaded lyrics is located in this repository [(here).](Lyrics_TaylorSwift.json) <br/><br/> 

#### 3. Create Pandas dataframe, clean data and tokenize lyrics: 
First, import the JSON file and create a Pandas dataframe with the various important fields as columns. Each row represents one song. After that, clean the data by getting rid of songs without lyrics, songs without album, songs which are actually interviews or speeches rather than songs, etc. <br/><br/> The next steps consist on removing punctuation, expanding contractions that are common in the English language, removing stopwords and tokenizing the lyrics of the songs. <br/><br/> In this section, several lookup tools are incorporated as well, such as being able to find songs by a specific word, find songs by album, etc. I added this as I was interested in finding what songs contained certain words, and whether certain albums contained certain lyrics since songs in an album are often thematically similar and because there are some themes (such as colours, elements from nature, etc) that Taylor Swift has used throughout her career. <br/><br/>

#### 4. Create visualizations of the song lyrics: 
In particular, produce horizontal barplots of n-grams for the most common words used in all the songs and for each of the full studio albums (note that stopwords have been removed). A n-gram is a contiguous sequence of n words from a given document, which in this case the document consists of the lyrics of a song. In this project, I will be looking at one word (unigrams), two words (bigrams) and three words (trigrams) n-grams. <br/><br/> The barplots of the n-grams (see below) are very interesting as they show that some albums have more repetition of words than others. For instance, 1989, which is the album that leans the most into the pop genre, has the highest repetition of words in terms of individual words, bigrams and trigrams. This makes sense as pop songs tend to have catchy and repetitive choruses. <br/><br/>

Barplots of top unigrams per album:

<img src="https://github.com/martaaliu/Song-Lyrics-NLP/blob/main/Images/Unigrams.png?raw=true" width="720">
<br/>

Barplots of top bigrams per album:

<img src="https://github.com/martaaliu/Song-Lyrics-NLP/blob/main/Images/Bigrams.png?raw=true" width="720">
<br/>

Barplots of top trigrams per album:

<img src="https://github.com/martaaliu/Song-Lyrics-NLP/blob/main/Images/Trigrams.png?raw=true" width="720">
<br/>

#### 5. Produce word embeddings of the song lyrics with Word2vec: 
The algorithm Word2vec from the Gensim library is used to create embeddings of the song lyrics. Once the model is trained, certain analysis can be performed such as finding the most similar words to a selected word. <br/><br/> This algorithm is very powerful, however, it needs a lot of input data. The dataset used contained only Taylor Swift lyrics, which, once cleaned, consisted of 3850 unique words. This is a very small dataset to train the model using Word2vec and, as such, the model did not perform as well as expected.

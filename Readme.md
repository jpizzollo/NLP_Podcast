# Overview

This project uses natural language processing and topic modeling to identify topics discussed in the TrainerRoad cycling podcast. This podcast is a mix of question and answer segments, discussion among hosts, and interviews with guest. The goal of this project was to determine which topics were discussed at different time points throughout podcast episodes and identify conversations that incorporate multiple topics.

# Data Collection
A set of podcast episodes was identified in a 153 episode playlist on YouTube. Video IDs for each episode were scraped using BeautifulSoup and Selenium in addition to metadata for upload date, views, likes, and dislikes. Transcripts were collected from the YouTube transcripts API using video IDs as keys. In total, transcripts for 141 episodes were collected.

# Data Preprocessing
Transcripts from YouTube contain timestamps, which were used to group text into 5 minute documents. The corpus was tokenized using the spaCy English core module and data were filtered to exclude all parts of speech other than lemmatized nouns and adjectives. This filtered set was vectorized with the scikit-learn CountVectorizer, removing English stop words and limiting term document frequency to a maximum of 0.3.

# Topic Modeling
To identify topics in each document, a latent Dirichlet allocation model was applied to the vectorized document-term matrix. The number of components used in constructing the model was determined by constructing models with 10 to 30 components and manually inspecting how terms were distributed among topics. The number of components was chosen to maximize the number distinct topics while minimizing the number of components that contain nonspecific topics.

# BBC News Category Prediction

This project is a text classification pipeline to predict the category of BBC news articles. The categories include:
- Business  
- Entertainment  
- Politics  
- Tech  
- Sport  

The model is built using Python, TensorFlow/Keras, and NLP preprocessing techniques.

## Dataset
- Columns:
  - `category` : Category of news article
  - `filename` : Original file name
  - `title`    : Title of the article
  - `content`  : Full text of the article  

- Example record:

| category | filename | title                     | content                         |
|----------|---------|---------------------------|---------------------------------|
| business | 001.txt | Ad sales boost Time Warner | Quarterly profits at US media...|

- Category distribution:
sport: 511
business: 510
politics: 417
tech: 401
entertainment: 386

- No missing values were found.

## Data Preprocessing

1. **Stopwords Removal**  
   - Removed common filler words using NLTK stopwords.

2. **Text Cleaning**  
   - Converted text to lowercase and removed punctuation using regex.  

3. **Feature Creation**  
   - Cleaned content stored in `content_clean`.  

4. **Visualization**  
   - Count plot of categories.  
   - Word clouds for each category based on titles to see important words.

## Model Preparation

1. **Train-Test Split**  
   - 80% training, 20% testing.  
   - Ensured balanced distribution across categories.

2. **Tokenization & Padding**  
   - Converted text to sequences using `Tokenizer`.  
   - Applied padding to `max_length = 256`.

3. **Label Encoding**  
   - Categories converted to numerical labels.

## Model Architecture

- **Embedding Layer**: Maps words to dense vectors (dimension = 32)  
- **GlobalAveragePooling1D**: Averages embeddings into fixed-length vector  
- **Dense Layer**: 128 neurons with ReLU activation  
- **Output Layer**: Softmax activation to predict 5 categories  

## Conclusion
- The model accurately classifies BBC news articles into their respective categories.
- NLP preprocessing combined with embeddings and a neural network provides high accuracy.
- This approach can be extended to any text classification problem.

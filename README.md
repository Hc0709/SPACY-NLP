
# NLP Tokenization, Stop Words, Synonyms, and Antonyms

This project demonstrates various Natural Language Processing (NLP) techniques using Spacy and NLTK libraries in Python. The focus is on tokenization, stop words removal, and working with synonyms and antonyms.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
  - [Tokenization](#tokenization)
  - [Stop Words Removal](#stop-words-removal)
  - [Synonyms and Antonyms](#synonyms-and-antonyms)
- [Contributing](#contributing)
- [License](#license)

## Installation

Before running the code, make sure you have the required libraries installed. You can install them using pip:

```bash
pip install spacy
pip install nltk
python -m spacy download en_core_web_lg
```

## Usage

The project consists of different sections for tokenization, stop words removal, and finding synonyms and antonyms.

### Tokenization

Tokenization is the process of splitting text into individual tokens. This can be done at the word level or sentence level.

#### Word Tokenization with Spacy

```python
import spacy

nlp = spacy.load('en_core_web_lg')
text = nlp('Gfg is looking for ds interns')
for token in text:
    print(token)
```

#### Sentence Tokenization with Spacy

```python
txt = nlp('this is sen1. this is sen2. this is sen3. lets study now')
for sent in txt.sents:
    print(sent)
```

#### Sentence and Word Tokenization with NLTK

```python
import nltk
nltk.download('punkt')
from nltk import sent_tokenize, word_tokenize

print(sent_tokenize('this is sen1. this is sen2. this is sen3. lets study now'))
print(word_tokenize('this is sen1. this is sen2. this is sen3. lets study now'))
```

### Stop Words Removal

Stop words are common words that are usually filtered out in NLP tasks.

#### Displaying and Modifying Stop Words in Spacy

```python
import spacy

nlp = spacy.load('en_core_web_sm')
print(nlp.Defaults.stop_words)

# Adding a custom stop word
nlp.Defaults.stop_words.add('i.e')
nlp.vocab['i.e'].is_stop = True

# Removing a custom stop word
nlp.Defaults.stop_words.remove('i.e')
nlp.vocab['i.e'].is_stop = False
```

#### Removing Stop Words from Text

```python
t = '''Data science is the study of data to extract meaningful insights for business. ... '''
t = t.replace('\n','').strip()
corp = nlp(t)

filtered_text = " ".join([token.text for token in corp if not token.is_stop])
print(filtered_text)
```

### Synonyms and Antonyms

Finding synonyms and antonyms using NLTK's WordNet.

#### Synonyms

```python
import nltk
from nltk.corpus import wordnet

nltk.download('wordnet')
nltk.download('omw-1.4')

synonyms = []
for syn in wordnet.synsets('happy'):
    for lemma in syn.lemmas():
        synonyms.append(lemma.name())
print(synonyms)
```

#### Antonyms

```python
antonyms = []
for syn in wordnet.synsets('good'):
    for lemma in syn.lemmas():
        if lemma.antonyms():
            antonyms.append(lemma.antonyms()[0].name())
print(antonyms)
```

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue.

## License

This project is licensed under the MIT License.


<H1 ALIGN =CENTER>Implementation of Semantic Analysis</H1>
<H3>NAME: Vinush CV</H3>
<H3>REGISTER NO: 212222230176</H3>
<H3>EX. NO.6</H3>
<H3>DATE:09/9/2024</H3>
<H3>Aim:  </H3>  To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques.
<h3>Algorithm:</h3>

1. Import the nltk library.
2. Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.
3. Accept user input for the text.
4. Tokenize the input text into words using the word_tokenize function.
5. Iterate through each word in the tokenized text.
   - Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
   - Print each word along with its corresponding part-of-speech tag.<br>
   - For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
   - Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
   - Print the unique sets of synonyms and antonyms.

<H3>Program:</H3>

```py
!pip install nltk

import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')


f = open("/content/sample_data.txt", "r")
sentences = f.readlines()
f.close()
verbs = [[] for _ in sentences]
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)

  # Tokenize the sentence into words
  words = word_tokenize(sentence)

  # Identify the parts of speech for each word
  pos_tags = nltk.pos_tag(words)

  # Print the parts of speech
  for word,tag in pos_tags:
    print(word,"->",tag)

    # Save verbs
    if tag.startswith('VB'):
      verbs[i].append(word)
  i+=1
  print("\n\n") 

# Identify synonyms and antonyms for each word
print("Synonyms and Antonymns for verbs in each sentence:\n")
i=0
for sentence in sentences:
  print("Sentence",i+1,":", sentence)
  pos_tags = nltk.pos_tag(verbs[i])
  for word,tag in pos_tags:
    print(word,"->",tag)
    synonyms = []
    antonyms = []
    for syn in wordnet.synsets(word):
      for lemma in syn.lemmas():
        synonyms.append(lemma.name())
        if lemma.antonyms():
          for antonym in lemma.antonyms():
            antonyms.append(antonym.name())

    # Print the synonyms and antonyms
    print("Synonyms:",set(synonyms))
    print("Antonyms:", set(antonyms) if antonyms else "None")
    print()
  print("\n\n")
  i+=1
```

<H3>Output</H3>
<h4>Words and the respective POS-Tags </h4>

![image](https://github.com/user-attachments/assets/1f5bf75a-4ca0-4ee5-9908-ce4f40f25dd6)
<h4>Synonyms and Antonyms for verbs in each sentence</h4>

![image](https://github.com/user-attachments/assets/90bbbb0b-5c94-4089-a94a-73a3f816604d)
<H3>Result:</H3>
Thus, the program to perform the Parts of Speech identification and Synonymis was executed successfully.

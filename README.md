Precision: 0.8518099547511312 Recall: 0.6657824933687002 F-score: 0.747394540942928 with sentencepiece.
test data is from https://github.com/neubig/kytea/blob/master/tools/kytea-active/data/wiki-sample.word
I used the first 100 lines for testing.

I used smaller_large_corpus.txt(download from https://www.rondhuit.com/download.html#ldcc) to train and used vocab size 2000. I got Precision: 0.8947963800904978
Recall: 0.8505376344086022
F-score: 0.8721058434399118
quite nice score tbh.

with top.txt and 3000 vocab size, I got Precision: 0.8823529411764706
Recall: 0.759493670886076
F-score: 0.8163265306122448
not bad.

Vocab size would be a significant factor.



For apertium-jpn, there is a python file called modCov.py. It tokenize text file with tokeniser.py and evaluation is calculated with untokenized/total. 
It got 42.22% with Hiroshima file. On tests file, python3 modCov.py ~/Desktop/gsoc/apertium-jpn/jpn.automorf.bin ~/Desktop/gsoc/jpn-corpus/Hiroshima_Peace_Park_Wikipedia.txt output the accuracy.

For sentence.py, I simply tried word segmentation aspect and used Hiroshima file as an input. It produces model and vocaburary. With the model, i tokenized Hiroshima file and i got 62.11% with some words from lexc file in apertium-jpn.
word segmentation doc in python https://pypi.org/project/sentencepiece/
I got 85.24% with bochan.txt input. Larger corpus input will make accuracy better.

Brief summary of Sentencepiece:'SentencePiece' solves problem by using 'subwords'. First, the text is split into words and the frequency of each word is determined. High frequency words are then treated as a single vocabulary, while low frequency words are split into shorter vocabulary words. The splitting is then repeated until the vocabulary number reaches a pre-specified number. This makes it possible to eliminate unknown words while keeping the vocabulary size small.


For speed comparison, I used bochan.txt, which is fairly large japanese corpus. I got initinal speed with only one japanese word. 

Below is screenshot of sentencepiece word segmentation(62%)

![Screenshot from 2023-06-22 09-03-49](https://github.com/yypy22/gsoc_try/assets/99264752/e9615d7a-4eac-4845-abaf-d12327a9a828)

Below is with 85% one
![Screenshot from 2023-06-23 00-44-55](https://github.com/yypy22/gsoc_try/assets/99264752/d5f456b4-c0f7-4001-aca7-6a3d8464b37a)

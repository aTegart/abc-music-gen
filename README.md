# abc-music-gen

This project is a Jupyter notebook, hosted on Google Colab. You can open a copy of this notebook in Colab by clicking the badge below.

<a href="https://colab.research.google.com/github/aTegart/abc-music-gen/blob/main/D3.ipynb">![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)</a>

abc-music-gen uses an [LSTM RNN](https://www.tensorflow.org/api_docs/python/tf/keras/layers/LSTM) to learn music in [ABC notation](http://abcnotation.com/blog/2010/01/31/how-to-understand-abc-the-basics/) and to generate its own music. We are training on a collection of Canadian folk music collected from [JC's ABC Tune Finder](http://trillian.mit.edu/~jc/cgi/abc/tunefind), [Traditional Tune Archive](https://tunearch.org/wiki/TTA), and the [Montreal Session Tunebook](https://www.montrealsession.ca/listing.php?title=Quebec&book=quebec.abc), though this code can be used with any music represented in ABC notation. ABC can be generated in any desired length, though more than one song may be included in the generated text.

The produced LSTM model is evaluated on the basis of how well it can predict the next character in a song (from a validation set), given a seed comprised of a songs's metadata (which can include title, key, time signature, etc) and the first few bars of the song itself.

This notebook requires the following python libraries:
- google.colab
- matplotlib
- numpy
- os
- tensorflow
- tqdm

To run the code, make sure your ABC songs are stored in Google Drive. Mount your Google Drive to Colab by running the top code cell and authenticating. Adjust the filepath `mypath` to match the location of your songs. You can now sequentially execute the rest of the code cells.

An example of an output song:
```X:80
T:Reel Bélangive Brunet
Z:robin.beech@mcgill.ca
R:reel
M:2/4
L:1/16
K:D
BA |BAB G2B | GFBd e2d2 |
dfB(3ECE ce | (3BGB AG |1 (3cdc Bd GBBd |:
AB(3cBA ed cdec |1 dafg afdf a4 |
ABGB AFDF | ECDD DFB,D CEFG | FAGF DFEF :|2cBAG EDEF |
GBGB A2|: G2B2 dBGB|AFAB =FABc|1"G"Bcdf a4 FAdA|FABc d2Ac | defg a2eg|!
GABc dfcA|AG ~B2 BfcB|1AG|"D"F2F2E2 |
|: FGAB cABA | GABG FAD
FAdB aaee | f2fd e2ce | fefg addd edBG |
AB(3eee eE |
FAdf gedg :|2 a2e2 f2a2 | (ABcA ^GB |\
"F"D4- D3F | fafd d3A 
```

Generated songs can be copied into an ABC-to-MIDI converter, like https://colinhume.com/Music.aspx, to produce audio files and sheet music.

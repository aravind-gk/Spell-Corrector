# Spell-Corrector
A basic spell correction python program which I wrote in 30 minutes as part of a hands-on coding round at a startup.

The algorithm is as follows:
- Given both the clean and unclean (containing mis-spelled words) sentences, create a vocabulary of known & correct words -- set of all words from the clean sentences
- For all words in vocabulary, create and store their _count-vectors_, of size (26x1).
- For each unclean sentence, split them into individual words and for each word, do the following -
    - If that word is present in our vocabulary of clean words, it's already correct.
    - Else, create a _count-vector_ embedding of size (26x1) for that word
    - Compare the cosine similarity of this word with all words in vocabulary to find the closest match. Then output this highest-similarity match as the clean, corrected spelling for given mis-spelled word.

This very basic and simple algorithm works surprisingly well for most practical situations, but also has some obvious drawbacks -
- Using this method, we cannot differentiate between words having different spellings but identical count-vectors.
- The exact position and semantics cannot be captured using count-vectors.
- This model will struggle with words which have different spellings in different regions, like _color_ and _colour_.
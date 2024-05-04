---
title: "Rune Frequency"
layout: post
date: 2024-4-30
tag:
- phonemes
category: blog
description: The Frequency of Runes in the Rune School Spelling System
hidden: false
---

Which are the runes that are most common in the Rune School Spelling System?

Since the spelling is largely based on the Shavian [ReadLex](https://readlex.pythonanywhere.com/spellingprinciples/) standard, we should be able to use that as a base of information to determine this.

@kj7qlv in the Rune School discord server wrote a script that analyzes the IPA spelling in the Shavian ReadLex dictionary directly. This way we can get the data on things like our "happY" rune ᛄ.

```python
import pandas as pd
import re

# Sample regular expressions and phonemes data
phonemes = {
    re.compile(r'(?<![aeɔ])ɪ'): {'ᛁ': 1},
    re.compile(r'i(?!ː)'): {'ᛄ': 1},
    re.compile(r'e(?!ə)'): {'ᛖ': 1},
    re.compile(r'æ'): {'ᚫ': 1},
    re.compile(r'ɒ(?!ː)'): {'ᚩ': 1},
    re.compile(r'ɔːR'): {'ᚩ': 1, 'ᚱ': 1},
    re.compile(r'ʊ'): {'ᚣ': 1},
    re.compile(r'ʊəR'): {'ᚣ': 1, 'ᚱ': 1},
    re.compile(r'ʌ'): {'ᚢ': 1},
    re.compile(r'ɜːR'): {'ᚢ': 1, 'ᚱ': 1},
    re.compile(r'ə(?!R)|I'): {'ᛟ': 1},
    re.compile(r'əR'): {'ᛟ': 1, 'ᚱ': 1},
    re.compile(r'iə(?!R)'): {'ᛠ': 1},
    re.compile(r'iəR'): {'ᛠ': 1, 'ᚱ': 1},
    re.compile(r'eəR'): {'ᛖ': 1, 'ᚱ': 1},
    re.compile(r'(ɑː|Ɑ)(?!R)'): {'ᚪ': 1},
    re.compile(r'(ɑː|Ɑ)R'): {'ᚪ': 1, 'ᚱ': 1},
    re.compile(r'ɔː'): {'ᚩ': 2},
    re.compile(r'iː'): {'ᛇ': 1},
    re.compile(r'eɪ'): {'ᛖ': 1, 'ᛡ': 1},
    re.compile(r'aɪ'): {'ᚫ': 1, 'ᛡ': 1},
    re.compile(r'ɔɪ'): {'ᚩ': 1, 'ᛡ': 1},
    re.compile(r'aʊ'): {'ᚫ': 1, 'ᚹ': 1},
    re.compile(r'əʊ'): {'ᚩ': 1, 'ᚹ': 1},
    re.compile(r'uː'): {'ᚣ': 1, 'ᚹ': 1},
    re.compile(r'p'): {'ᛈ': 1},
    re.compile(r'b'): {'ᛒ': 1},
    re.compile(r't(?!ʃ)'): {'ᛏ': 1},
    re.compile(r'd'): {'ᛞ': 1},
    re.compile(r'k'): {'ᛣ': 1},
    re.compile(r'(ɡ|g)'): {'ᚸ': 1},
    re.compile(r'f'): {'ᚠ': 1},
    re.compile(r'v'): {'v': 1},
    re.compile(r'(θ|ð|Ð)'): {'ᚦ': 1},
    re.compile(r's'): {'ᛋ': 1},
    re.compile(r'z'): {'ᛉ': 1},
    re.compile(r'(?<!t)ʃ'): {'ᛋ': 1, 'ᚳ': 1},
    re.compile(r'(?<!d)ʒ'): {'ᛉ': 1, 'ᚳ': 1},
    re.compile(r'tʃ'): {'ᚳ': 1},
    re.compile(r'dʒ'): {'ᚷ': 1},
    re.compile(r'j'): {'ᛡ': 1},
    re.compile(r'w'): {'ᚹ': 1},
    re.compile(r'ŋ'): {'ᛝ': 1},
    re.compile(r'h'): {'ᚻ': 1},
    re.compile(r'l'): {'ᛚ': 1},
    re.compile(r'r'): {'ᚱ': 1},
    re.compile(r'm'): {'ᛗ': 1},
    re.compile(r'n'): {'ᚾ': 1}
}

# Initialize running_total dictionary
running_total = {}

# Function to update running_total based on phonemes match
def update_running_total(phoneme_dict, frequency, weighted: bool):
    for key, value in phoneme_dict.items():
        value =  value * frequency if weighted else value
        if key in running_total:
            running_total[key] += value
        else:
            running_total[key] = value

# Function to initialize readlex DataFrame from TSV file
def initialize_readlex(file_path):
    try:
        readlex_df = pd.read_csv(file_path, sep='\t', header=None, usecols=[3, 4])
        readlex_df.columns = ['Pronunciation', 'Frequency']
        return readlex_df
    except Exception as e:
        print(f"Error occurred while initializing readlex: {e}")
        return None

# Sample data for testing
readlex_df = initialize_readlex('./kingsleyreadlexicon.tsv')
if readlex_df is not None:
    # Iterate through readlex
    for index, row in readlex_df.iterrows():
        pronunciation = row['Pronunciation']
        frequency = row['Frequency']
        
        # Check against all keys in phonemes
        for regex, phoneme_dict in phonemes.items():
            matches = regex.findall(pronunciation)
            for match in matches:
                update_running_total(phoneme_dict, frequency, weighted=False)

running_total_sum = sum(running_total.values())
for key, value in running_total.items():
    running_total[key] = value / running_total_sum
running_total_sorted = dict(sorted(running_total.items(), key=lambda item: item[1], reverse=True))
print(running_total_sorted)
```

## With All Runes

So here is the data with all of the runes except for ᛥ and ᛢ.

| Order | Runes w/ Shortcuts | Unweighted Value |
| ----- | ------------------ | ---------------- |
| 1     | ᛟ                  | 8.49%            |
| 2     | ᚱ                  | 7.12%            |
| 3     | ᛁ                  | 6.71%            |
| 4     | ᛋ                  | 6.50%            |
| 5     | ᛏ                  | 5.92%            |
| 6     | ᛖ                  | 5.44%            |
| 7     | ᚾ                  | 5.16%            |
| 8     | ᛞ                  | 4.87%            |
| 9     | ᚩ                  | 4.59%            |
| 10    | ᛚ                  | 4.55%            |
| 11    | ᛡ                  | 3.96%            |
| 12    | ᚫ                  | 3.87%            |
| 13    | ᛣ                  | 3.81%            |
| 14    | ᛉ                  | 3.20%            |
| 15    | ᚹ                  | 3.06%            |
| 16    | ᛈ                  | 2.65%            |
| 17    | ᚣ                  | 2.64%            |
| 18    | ᛗ                  | 2.49%            |
| 19    | ᛒ                  | 1.83%            |
| 20    | ᚢ                  | 1.70%            |
| 21    | ᛝ                  | 1.66%            |
| 22    | ᚠ                  | 1.52%            |
| 23    | ᚳ                  | 1.49%            |
| 24    | ᛄ                  | 1.15%            |
| 25    | ᛇ                  | 1.14%            |
| 26    | ᚸ                  | 1.06%            |
| 27    | ![FF Bindrune](/assets/images/ff-bindrune.png)   | 1.01%            |
| 28    | ᚪ                  | 0.69%            |
| 29    | ᚷ                  | 0.65%            |
| 30    | ᚻ                  | 0.62%            |
| 31    | ᚦ                  | 0.36%            |
| 32    | ᛠ                  | 0.09%            |

| Order | Runes w/ Shortcuts | Weighted Value |
| ----- | ------------------ | -------------- |
| 1     | ᛟ                  | 8.18%          |
| 2     | ᛁ                  | 6.67%          |
| 3     | ᚱ                  | 6.63%          |
| 4     | ᚾ                  | 5.91%          |
| 5     | ᛏ                  | 5.85%          |
| 6     | ᛋ                  | 5.46%          |
| 7     | ᚩ                  | 5.43%          |
| 8     | ᛖ                  | 5.33%          |
| 9     | ᚹ                  | 4.16%          |
| 10    | ᚫ                  | 3.90%          |
| 11    | ᛡ                  | 3.87%          |
| 12    | ᛞ                  | 3.70%          |
| 13    | ᛚ                  | 3.70%          |
| 14    | ᚦ                  | 3.32%          |
| 15    | ᚣ                  | 3.08%          |
| 16    | ᛣ                  | 2.94%          |
| 17    | ᛉ                  | 2.77%          |
| 18    | ᛗ                  | 2.57%          |
| 19    | ᛈ                  | 1.99%          |
| 20    | ᚢ                  | 1.92%          |
| 21    | ᛒ                  | 1.71%          |
| 22    | ᛇ                  | 1.68%          |
| 23    | ᚳ                  | 1.51%          |
| 24    | ᚠ                  | 1.42%          |
| 25    | ᚻ                  | 1.31%          |
| 26    | ᛄ                  | 1.11%          |
| 27    | ![FF Bindrune](/assets/images/ff-bindrune.png)   | 1.11%          |
| 28    | ᛝ                  | 0.86%          |
| 29    | ᚸ                  | 0.73%          |
| 30    | ᚪ                  | 0.64%          |
| 31    | ᚷ                  | 0.53%          |
| 32    | ᛠ                  | 0.02%          |

You can compare similar analysis done [in Shavian](https://www.reddit.com/r/shavian/comments/ovke9g/shavian_letter_frequencies/).

Note that Shavian often assumes that you pronounce words like "lot" with ᚩ, but most Americans would probably use ᚪ for this sound, boosting it up in percentage.

## Without Shortcut Runes

If we got rid of the shortcut runes (ᛇᛠᚪ and double-feoh), the data becomes the following. This might be useful for a game like Scrabble, for example.

| Order | Runes w/o Shortcuts | Unweighted value |
| ----- | ------------------- | ---------------- |
| 1     | ᛟ                   | 8.25%            |
| 2     | ᛁ                   | 7.90%            |
| 3     | ᚱ                   | 7.00%            |
| 4     | ᛋ                   | 6.38%            |
| 5     | ᛏ                   | 5.81%            |
| 6     | ᛖ                   | 5.43%            |
| 7     | ᚫ                   | 5.16%            |
| 8     | ᚾ                   | 5.07%            |
| 9     | ᛡ                   | 5.00%            |
| 10    | ᛞ                   | 4.78%            |
| 11    | ᚩ                   | 4.51%            |
| 12    | ᛚ                   | 4.47%            |
| 13    | ᛣ                   | 3.74%            |
| 14    | ᛉ                   | 3.14%            |
| 15    | ᚹ                   | 3.00%            |
| 16    | ᛈ                   | 2.60%            |
| 17    | ᚣ                   | 2.59%            |
| 18    | ᚠ                   | 2.49%            |
| 19    | ᛗ                   | 2.44%            |
| 20    | ᛒ                   | 1.80%            |
| 21    | ᚢ                   | 1.67%            |
| 22    | ᛝ                   | 1.63%            |
| 23    | ᚳ                   | 1.46%            |
| 24    | ᚸ                   | 1.04%            |
| 25    | ᛄ                   | 1.04%            |
| 26    | ᚷ                   | 0.63%            |
| 27    | ᚻ                   | 0.61%            |
| 28    | ᚦ                   | 0.35%            |

| Order | Runes w/o Shortcuts | Weighted Value |
| ----- | ------------------- | -------------- |
| 1     | ᛁ                   | 8.19%          |
| 2     | ᛟ                   | 7.96%          |
| 3     | ᚱ                   | 6.47%          |
| 4     | ᚾ                   | 5.76%          |
| 5     | ᛏ                   | 5.70%          |
| 6     | ᛖ                   | 5.47%          |
| 7     | ᛡ                   | 5.41%          |
| 8     | ᛋ                   | 5.32%          |
| 9     | ᚩ                   | 5.29%          |
| 10    | ᚫ                   | 5.04%          |
| 11    | ᚹ                   | 4.06%          |
| 12    | ᛞ                   | 3.61%          |
| 13    | ᛚ                   | 3.61%          |
| 14    | ᚦ                   | 3.23%          |
| 15    | ᚣ                   | 3.00%          |
| 16    | ᛣ                   | 2.87%          |
| 17    | ᛉ                   | 2.70%          |
| 18    | ᛗ                   | 2.51%          |
| 19    | ᚠ                   | 2.46%          |
| 20    | ᛈ                   | 1.94%          |
| 21    | ᚢ                   | 1.87%          |
| 22    | ᛒ                   | 1.66%          |
| 23    | ᚳ                   | 1.47%          |
| 24    | ᚻ                   | 1.27%          |
| 25    | ᛄ                   | 1.06%          |
| 26    | ᛝ                   | 0.84%          |
| 27    | ᚸ                   | 0.71%          |
| 28    | ᚷ                   | 0.52%          |

# Findings

Overall, ᛟ and ᛁ are the most common vowels in the Rune School Spelling System by far. 

Of the three vowel sisters ᚫᚪᚩ, ᚫ and ᚩ will be about equally frequent with ᚪ being more rare. I think this is appropriate since ᚪ is in between the other two.

ᚩ is the first rune in terms of frequency that is unique to just the Anglo-Saxon runes. So if you're trying to determine which language is being written with some runes, you will likely notice ᚩ and know that it is English. Seeing ᛣ will be the next clue that you're reading English.

ᛝ is surprisingly low in this data. My guess is that common word derivations such as "-ᛁᛝ" or perhaps "-ᛉ" and "-ᛞ" are not taken into account.

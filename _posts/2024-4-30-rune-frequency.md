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

# How

Since the spelling is largely based on the Shavian [ReadLex](https://readlex.pythonanywhere.com/spellingprinciples/) standard, we should be able to use that as a base of information to determine this.

@kj7qlv in the [Rune School discord server](https://discord.gg/BThW4fxAwN) wrote a script that analyzes the IPA spelling in the Shavian ReadLex dictionary directly. This way we can get the data on things like our "happY" rune ᛄ.

```python
import pandas as pd
import re
import argparse

# Setup argument parser to accept flags
parser = argparse.ArgumentParser(description='Calculate the most common runes for the Rune School Spelling System.')
parser.add_argument('--weighted', action='store_true', help='Apply weighting based on frequency')
parser.add_argument('--shortcuts', action='store_true', help='Use shortcut runes ᛇᛠᚪ')
parser.add_argument('--v', action='store_true', help='Use the Double Feoh bindrune for /v/ phoneme')
parser.add_argument('--kw', action='store_true', help='Use Cweorth rune for /kw/ phoneme')
parser.add_argument('--st', action='store_true', help='(Naively) Use Stan rune for /st/ phoneme')

# Parse the command line arguments
args = parser.parse_args()

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
    re.compile(r'iə(?!R)'): {'ᛠ': 1} if args.shortcuts else {'ᛁ': 2},
    re.compile(r'iəR'): {'ᛠ': 1, 'ᚱ': 1} if args.shortcuts else {'ᛁ': 2, 'ᚱ': 1},
    re.compile(r'eəR'): {'ᛖ': 1, 'ᚱ': 1},
    re.compile(r'(ɑː|Ɑ)(?!R)'): {'ᚪ': 1} if args.shortcuts else {'ᚫ': 2},
    re.compile(r'(ɑː|Ɑ)R'): {'ᚪ': 1, 'ᚱ': 1} if args.shortcuts else {'ᚫ': 2, 'ᚱ': 1},
    re.compile(r'ɔː'): {'ᚩ': 2},
    re.compile(r'iː'): {'ᛇ': 1} if args.shortcuts else {'ᛁ': 1, 'ᛡ': 1},
    re.compile(r'eɪ'): {'ᛖ': 1, 'ᛡ': 1},
    re.compile(r'aɪ'): {'ᚫ': 1, 'ᛡ': 1},
    re.compile(r'ɔɪ'): {'ᚩ': 1, 'ᛡ': 1},
    re.compile(r'aʊ'): {'ᚫ': 1, 'ᚹ': 1},
    re.compile(r'əʊ'): {'ᚩ': 1, 'ᚹ': 1},
    re.compile(r'uː'): {'ᚣ': 1, 'ᚹ': 1},
    re.compile(r'p'): {'ᛈ': 1},
    re.compile(r'b'): {'ᛒ': 1},
    re.compile(r'st'): {'ᛥ': 1} if args.st else {'ᛋ': 1, 'ᛏ': 1},
    re.compile(r't(?!ʃ)'): {'ᛏ': 1},
    re.compile(r'd'): {'ᛞ': 1},
    re.compile(r'kw'): {'ᛢ': 1} if args.kw else {'ᛣ': 1, 'ᚹ': 1},
    re.compile(r'k'): {'ᛣ': 1},
    re.compile(r'(ɡ|g)'): {'ᚸ': 1},
    re.compile(r'f'): {'ᚠ': 1},
    re.compile(r'v'): {'v': 1} if args.v else {'ᚠ': 1},
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
        value = value * frequency if weighted else value
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
                update_running_total(phoneme_dict, frequency, weighted=args.weighted)

running_total_sum = sum(running_total.values())
for key, value in running_total.items():
    running_total[key] = value / running_total_sum
running_total_sorted = dict(sorted(running_total.items(), key=lambda item: item[1], reverse=True))
print(running_total_sorted)
```

If you put the [kingsleyreadlexicon.tsv](https://github.com/Shavian-info/readlex/blob/main/kingsleyreadlexicon.tsv) dictionary in the same directory as this script and do the command `python script.py --help` you will see the following:

```console
usage: script.py [-h] [--weighted] [--v] [--shortcuts] [--kw] [--st]

Calculate the most common runes for the Rune School Spelling System.

options:
  -h, --help   show this help message and exit
  --weighted   Apply weighting based on frequency
  --shortcuts  Use shortcut runes ᛇᛠᚪ
  --v          Use the Double Feoh bindrune for /v/ phoneme
  --kw         Use Cweorth rune for /kw/ phoneme
  --st         (Naively) Use Stan rune for /st/ phoneme
```

# Results

So here is the data with all of the runes except for ᛥ and ᛢ.

Unweighted means that the frequency of the word doesn't matter.

`python script.py --v --shortcuts`

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

Weighted means that the frequency of the word is taken into account. This data will reflect how often you will see runes in a novel, for example.

`python script.py --weighted --v --shortcuts`

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

## Findings

Overall, ᛟ and ᛁ are the most common vowels in the Rune School Spelling System by far. 

Of the three vowel sisters ᚫᚪᚩ, ᚫ and ᚩ will be about equally frequent with ᚪ being more rare. I think this is appropriate since ᚪ is in between the other two.

ᚩ is the first rune in terms of frequency that is unique to just the Anglo-Saxon runes. So if you're trying to determine which language is being written with some runes, you will likely notice ᚩ and know that it is English. Seeing ᛣ will be the next clue that you're reading English.

ᛝ is surprisingly low in this data. My guess is that common word derivations such as "-ᛁᛝ" or perhaps "-ᛉ" and "-ᛞ" are not taken into account.

# Scrabble

If we wanted to get data for a game like Scrabble, we could get rid of the shortcut runes (ᛇᛠᚪ) and only consider the unweighted frequency. This would ensure a much more even frequency distribution, which I think is what we would want for this game.

`python script.py --v`

| Order | Runes w/o Shortcuts | Unweighted value         |
|-------|-----------|-------------------|
| 1     | ᛟ         | 8.104%            |
| 2     | ᛁ         | 7.673%            |
| 3     | ᛋ         | 7.399%            |
| 4     | ᛏ         | 6.847%            |
| 5     | ᚱ         | 6.799%            |
| 6     | ᛖ         | 5.190%            |
| 7     | ᚫ         | 5.016%            |
| 8     | ᚾ         | 4.927%            |
| 9     | ᛡ         | 4.861%            |
| 10    | ᛞ         | 4.648%            |
| 11    | ᚩ         | 4.383%            |
| 12    | ᛚ         | 4.345%            |
| 13    | ᛣ         | 3.799%            |
| 14    | ᚹ         | 3.079%            |
| 15    | ᛉ         | 3.051%            |
| 16    | ᛈ         | 2.529%            |
| 17    | ᚣ         | 2.521%            |
| 18    | ᛗ         | 2.376%            |
| 19    | ᛒ         | 1.742%            |
| 20    | ᚢ         | 1.626%            |
| 21    | ᛝ         | 1.582%            |
| 22    | ᚠ         | 1.452%            |
| 23    | ᚳ         | 1.422%            |
| 24    | ᛄ         | 1.099%            |
| 25    | ᚸ         | 1.010%            |
| 26    | ![FF Bindrune](/assets/images/ff-bindrune.png) | 0.966%            |
| 27    | ᚷ         | 0.617%            |
| 28    | ᚻ         | 0.594%            |
| 29    | ᚦ         | 0.345%            |

Now to view this data in a [Scrabble Letter Distribution](https://en.wikipedia.org/wiki/Scrabble_letter_distributions) table, we can assign tile numbers and point values like so:

<table>
<caption>Rune distribution<br>(Number of tiles across, point values down)</caption>
<tbody>
<tr>
    <th></th>
    <th>×1</th>
    <th>×2</th>
    <th>×3</th>
    <th>×4</th>
    <th>×6</th>
    <th>×8</th>
</tr>
<tr>
    <th>1</th>
    <td></td>
    <td></td>
    <td></td>
    <td>ᛋ ᛏ ᚱ</td>
    <td>ᛖ ᚫ ᚩ</td>
    <td>ᛟ ᛁ</td>
</tr>
<tr>
    <th>2</th>
    <td></td>
    <td></td>
    <td>ᚾ ᛡ</td>
    <td>ᚹ ᚣ ᚢ</td>
    <td></td>
    <td></td>
</tr>
<tr>
    <th>3</th>
    <td>ᛄ ᛝ</td>
    <td>ᛉ</td>
    <td>ᛞ ᚳ ᛗ ᛒ</td>
    <td></td>
    <td></td>
    <td></td>
</tr>
<tr>
    <th>4</th>
    <td></td>
    <td></td>
    <td>ᛚ ᛣ ᛈ </td>
    <td></td>
    <td></td>
    <td></td>
</tr>
<tr>
    <th>5</th>
    <td>ᛣ</td>
    <td>ᚠ <img src="/assets/images/ff-bindrune.png" alt="FF Bindrune"></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
</tr>
<tr>
    <th>8</th>
    <td>ᚦ ᚻ ᚷ ᚸ</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
</tr>
</tbody>
</table>

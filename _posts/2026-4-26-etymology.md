---
title: "Uniting The Clans"
layout: post
date: 2026-4-26
category: blog
description: Developing a etymological writing system that all English dialects can use together
hidden: true
---

## What's not working?

The idea of a phonemic writing system has a ton of logic to it. See the [preface to the Rune School lessons](/_lessons/1/) for more on that.

But there are two major issues that phonemic systems run into. 

1. How do you accomodate all dialects? Yes, a phonemic system allows for variations of sounds, but there are many dialects where differences stray further.

2. Users need to understand phonemes in order to use it. In order to understand phonemes, users need to gain some skill in listening and classifying sounds.

Issue 2 is very much related to issue 1. When someone is asking how to write a word in a phonemic system, you must ask them questions about how they say it. They often think they are saying it one way, but they are saying it another. You often advise them to write it how they "think" they're saying it regardless of how they "really" say it.

I ran into these issues again and again with Rune School.

## A solution appears

One day, someone in the Rune School discord server explained that an etymological system could be better for these issues. 

I thought it was interesting, but I ultimately wrote it off. I went back to tinkering and tinkering and tinkering on the current Rune School system. At the time, I was researching new ways to make the system more intuitive and English-native. I was doing things like mapping out regular sound changes and assigning runes to connected sounds.

The more I worked on that, the more I realized that I was essentially re-inventing an etymological system from first principles. So I decided to revisit this person's idea. They had created a little chart that mapped all vowel phonemes that existed in Old English to Latin letter spellings. "Hey wait, didn't you say this *wasn't* phonemic?" Yes, I did. 

Really, all an etymological system does is rewind the clock as far back as we can reasonably go to create our phonemic foundation. Then we take a snapshot of that and keep it the same forever. "Why?" Two reasons.

1. Believe it or not, there are many English dialects still alive today that are offshoots of much older versions of English than General American or Received Pronounciation. In order to have one global writing standard for English, we need to go further back in time than we realize. 

2. The period of time known as "Middle English" was *wild*, orthographically speaking. There were many inconsistencies or plain errors that caught on in this time that we can easily fix if we just go back a bit further. 

Let's look at an example. Take the words Sew, So, Sow.

All of these words in the Rune School system would be spelled with ᚩᚹ or ᚩ‍ᚹ. But not all dialects or accents today consider these words to be the same phoneme or lexical set. Mainstream accents like General American simply have the [Tow-Toe Merger](https://en.wikipedia.org/wiki/Phonological_history_of_English_diphthongs#Toe%E2%80%93tow_merger).

Some accents would put Sew and Sow in one category and So in another. Notice that these aren't just different realizations of the same phoneme. They are two different categories entirely. Sure, Rune School could support spellings like ᚩᚩ for "Toe" words and ᚩᚹ for "Tow" words, but what about accents that don't consider Sew and Sow to be in the same lexical set? Believe it or not, there are dialects used today that consider these two to be in different categories as well!

The easiest way to include all dialects is to simply go further back in time. And when we do this, we arrive at, essentially, an etymological spelling system.

- Sew was originally Siw    
- Sow was originally Soaw 
- So was originally Swoa 

English speakers are already accustomed to making accomodations in this way. We all use "what" even though neither General American nor Received Pronunciation pronounce that word with an "a" sound.

## Arguing against myself

Isn't "what" part of the issue I explained in the preface of Rune School?

> Now, the original idea of an alphabet is simple; like a hammer. But today with English, the way that we use the alphabet (how we spell) has become something complicated; like a large factory machine for which we have lost the instructions.

80% of the words in this etymological system are not written super differently from our current "orthodox" spelling system. So what is required is just a re-framing of the value of English writing. If language is a technology to connect people together, then this system would be the most effective at doing that.

Is it more complicated? Perhaps slightly. But the benefit of potentially unifying all dialects together and increasing the connective power is worth it.

What about this next part in the preface?

> Fix our current Latin alphabet spelling? The amount of proposals to do so are countless. Ultimately, it would take a united effort of all English-speaking nations to enforce such a proposal. Even if that happened, would the people accept it? When you spell words a certain way your whole life, the words are like childhood friends. A government requiring you to change your spelling later in life is like killing your old friends!

> You could start using your preferred spelling change today, but it would be percieved by others as spelling mistakes. In order to be able to adopt a new spelling system and avoid the confusion with the current spelling system, a new alphabet (script) is needed.

I'm still correct about that. The difference is that because we are going back in time and correcting the errors that accrued in the past, the spellings in this system would be technically speaking *more* correct than the orthography that we have today.

> The only problem is, if an alphabet can be created arbitrarily, it can be changed arbitrarily. It has no tie to history to make it feel concrete. 

So it's taking the historical rootedness argument from the preface to its fullest. And if language is meant to connect people together, going further into history will also help to recover our shared heritage as English speakers. 

English is a blend of Germanic languages. Such a historic writing system would also serve to connect English with its own cousins, sisters, brothers, and ultimately its mother (Proto-Indo-European).

## What we did

I want to just *do* things, so I took the mapping of OE phonemes to latin letter spellings and I started making a dictionary file. Myself and the creator of this system started from the most common words, working our way down. 

We got ~1,000 words in the dictionary. I then exposed this dictionary via a [translation tool](https://rune.school/dictionary/translate-etym) so that we could generate sample sentences and get a feel for the system.

I then made a [Keyman keyboard](https://github.com/trosel/etym-spelling-keyboard) for typing and text prediction to help with spelling.

I then made a simple runic mapping to the latin letter spellings of this system. The runic mapping contains the same logic as the latin letter version, except it does not distinguish vowel length, which is accurate to how runes were used in history. 

What this means is that the runic version of the etymological system actually ends up being quite succint. It becomes like more of a shorthand.

## Examples

Modern Orthodox:
> I know that the twain will never meet, but I am looking forward to the day next summer.

Etym Latin:
> Ih cnoaw thæt the twœeyen will n·ea·f’r meet, b’·out ih ạm looc·ing fore·wạrd too the dæy neạh·’st sųmor.

Etym Runic:
> ᛁᚻ᛫ᚳᚾᚪᚹ᛫ᚦᚫᛏ᛫ᚦᛖ᛫ᛏᚹᛟᚷᛖᚾ᛫ᚹᛁᛚᛚ᛫ᚾᚫᚠᚱ᛫ᛗᛖᛏ᛬ᛒᚢᛏ᛫ᛁᚻ᛫ᛠᛗ᛫ᛚᚩᛣᛁᛝ᛫ᚠᚩᚱᛖᚹᛠᚱᛞ᛫ᛏᚩ᛫ᚦᛖ᛫ᛞᚫᚷ᛫ᚾᛠᚻᛋᛏ᛫ᛋᚢᛗᚩᚱ᛫


## Status

This is still very much early days. I have intentionally not shared the details of how this works yet. If you are interested in contributing, we want more people to ask questions and give feedback. So please come by the discord. The link is in the [About](/about) page of this website.


## Random thoughts

- A cool added benefit of an etymological spelling system is that if "spelling pronunciation" continues as a trend, English speakers could very well recover old pronunciations that used to exist. Some isolated people could just read a lot in this orthography and eventually their pronunciations would get much closer to the original Old English phonemes! Or at least the original "lexical sets" for words could be recovered.

- The Latin version encodes more information than the Runic version. For that reason, the Latin forms are helpful for learning and finding connections across pronunciations. It's also just closer to what we are used to today. But the Runic being more succinct, it boils words down to their essential forms. Not "ᛋᛚᛖᛖᛈ" but "ᛋᛚᛖᛈ". Not "ᛋᚾᚩᚪᚹ" but "ᛋᚾᚪᚹ". These Runic forms could be useful almost as symbols; recognizable at a glance by native speakers. 

- Even though the runic etymological spellings are more simple (no vowel length), it surprisingly doesn't increase the amount of words that are spelled the same. This is due to the lexical set organization of Old English and also the fact that there's a lot more letters that are silent today that weren't silent in the past.

---
title: "The Rune School Spelling System"
layout: post
date: 2024-4-12
tag:
- spelling system
category: blog
description: An explanation of the Rune School spelling system for Modern English Futhorc
hidden: false
---

The Rune School Spelling System is inspired by [Shavian](https://shavian.info), [Rune Revival](https://runerevival.online), [Lexical Sets for Actors](https://ecampusontario.pressbooks.pub/lexicalsets/chapter/introduction-2/), and [Dr Geoff Lindsey](https://www.youtube.com/@DrGeoffLindsey).

You can think of it as a runic Shavian with a few improvements like:

* letter design is historically rooted
* flexibility to seamlessly add or subtract phonemes as the user wishes
* transparently shows the relationships between phonemes with consistent use of combinatorial patterns
* a letter for the happY vowel

This document will explain the [system](#system) and the logic of the [choices](#choices) behind it.

# System

Based on the data from the [runes and their sounds](/runes-and-sounds/) and the info from [Dr. Lindsey's IPA symbols](/version-2/#lindsey-vowels), we can create a spelling system.

## Consonants

The consonants are straight forward.

| IPA | Shavian | Runes | Bindrune / Shortcut rune |
| --- | --- | --- | --- |
| p | 𐑐 | ᛈ |  |
| b | 𐑚 | ᛒ |   |
| t | 𐑑 | ᛏ |  |
| d | 𐑛 | ᛞ |   |
| k | 𐑒 | ᛣ |  |
| kw | 𐑒𐑢 | ᛢ |  |
| g | 𐑜 | ᚸ |   |
| f | 𐑓 | ᚠ |  |
| v | 𐑝 | ᚠ | ![ff bindrune](/assets/images/ff-bindrune.png)  |
| θ | 𐑔 | ᚦ |  |
| ð | 𐑞 | ᚦ |  |
| s | 𐑕 | ᛋ |  |
| st | 𐑕𐑑 | ᛥ |  |
| z | 𐑟 | ᛉ |  |
| ʃ | 𐑖 | ᛋᚳ | ![sch bindrune](/assets/images/sch-bindrune.png) |
| ʒ | 𐑠 | ᛉᚳ | ![zch bindrune](/assets/images/%E2%80%8Dzch-bindrune.png) |
| ʧ | 𐑗 | ᚳ |  |
| ʤ | 𐑡 | ᚷ |  |
| j | 𐑘 | ᛡ |  |
| w | 𐑢 | ᚹ |  |
| ʍ | 𐑣𐑢 | ᚻᚹ | ![hw bindrune](/assets/images/hw-bindrune.png) |
| ŋ | 𐑙 | ᛝ |  |
| h | 𐑣 | ᚻ |  |
| l | 𐑤 | ᛚ |  |
| r | 𐑮 | ᚱ |  |
| m | 𐑥 | ᛗ |  |
| n | 𐑯 | ᚾ |  |

## Vowels

Vowel phonemes are the things that tend to vary the most across accents, so they require a bit more work.

![Rune School Lexical Sets](/assets/images/RuneSchoolLexicalSets.png)

There are 7 rows which we can consider the "main" vowel runes. Each column applies predictable patterns onto each of the main runes. It's doubled, then it's given a /j/ glide, then it's given a /w/ glide.

There are many blank spaces in this chart. These blank spaces represent vowel phonemes that don't exist in modern English, but potentially could in the future, or perhaps did in the past.

We can condense and simplify the above chart by 

- removing uncommon lexical set definitions
- combining lexical sets that are commonly merged (GOAT-GOAL, NORTH-FORCE)
- removing unnecessary doubled letters like ᚩᚩᚱ and ᚣᚣᚱ (if there is nothing to the left, it can be pushed left)
- using shortcut runes

![Rune School Lexical Sets Simplified](/assets/images/RuneSchoolLexicalSets-Simplified.png)

The Rune School Spelling System is pretty much a point for point recreation of the [Shavian ReadLex Spelling Standard](https://readlex.pythonanywhere.com/spellingprinciples/).

The idea is that you can use the ReadLex dictionary and swap Shavian out for runes.

| Traditional IPA | Modern IPA | Lexical Set | Shavian | Runes | Bindrune / Shortcut rune |
| --- | --- | --- | --- | --- |  --- | 
| ə | ə | commA | 𐑩 | ᛟ |  |
| ər | ər | lettER | 𐑼 | ᛟᚱ | ![uhr bindrune](/assets/images/uhr-bindrune.png) |
| ʌ | ə́ | STRUT | 𐑳 | ᚢ |   |
| ɜː | ə́ːr | NURSE | 𐑻 | ᚢᚱ | ![ur bindrune](/assets/images/ur-bindrune.png) |
| ɪ | ɪ | KIT | 𐑦 | ᛁ |  |
| ɪə | ɪ́ː | NEAR Prime | 𐑾 | ᛁᛁ | ᛠ |
| ɪər | ɪ́ːr | NEAR | 𐑾 | ᛁᛁᚱ | ᛠᚱ |
| i | ɪj | happY | 𐑦 | ᛄ |  |
| iː | ɪj | FLEECE | 𐑰 | ᛁᛡ  | ᛇ |
| e | ɛ | DRESS | 𐑧 | ᛖ |  |
| eɪ | ɛj | FACE | 𐑱 | ᛖᛡ | ![ej bindrune](/assets/images/ej-bindrune.png) |
| er | ɛ́r | Merry | 𐑧𐑮 | ᛖᚱ |  |
| eə | ɛ́ːr | SQUARE | 𐑺 | ᛖᛖᚱ | ![er bindrune](/assets/images/er-bindrune.png) |
| æ | a | TRAP | 𐑨 | ᚫ |  |
| ær | ár | Marry | 𐑨𐑮 | ᚫᚱ |  |
| aɪ | ɑj | PRICE | 𐑲 | ᚫᛡ | ![aj bindrune](/assets/images/aj-bindrune.png) |
| aʊ | áw | MOUTH | 𐑬 | ᚫᚹ | ![aw bindrune](/assets/images/aw-bindrune.png) |
| ɑː | ɑː | PALM | 𐑭 | ᚫᚫ  | ᚪ |
| ɑːr | ɑːr | START | 𐑸 | ᚫᚫᚱ  | ᚪᚱ |
| ɒ | ɔ́ | LOT | 𐑪 | ᚩ |  |
| ɔɪ | ój | CHOICE | 𐑶 | ᚩᛡ | ![oj bindrune](/assets/images/oj-bindrune.png) |
| ɔː | óː | THOUGHT | 𐑷 | ᚩᚩ | ![oo bindrune](/assets/images/oo-bindrune.png) |
| ɔːr | óːr | NORTH/FORCE | 𐑹 | ᚩᚱ | ![or bindrune](/assets/images/or-bindrune.png) |
| əʊ | əw | GOAT | 𐑴 | ᚩᚹ | ![ow bindrune](/assets/images/ow-bindrune.png) |
| ʊ | ʉ́ | FOOT | 𐑫 | ᚣ |  |
| ʊə | ʉ́ː | CURE | 𐑫𐑼 | ᚣᚱ | ![yr](/assets/images/uir-bindrune.png) |
| uː | ʉ́w | GOOSE | 𐑵 | ᚣᚹ | ![yw bindrune](/assets/images/yw-bindrune.png) |
| juː | jʉ́w |  | 𐑿 | ᛡᚣᚹ |  |

### Bindrunes

While it's definitely possible to have bindrunes that have the same effect as the "compound" or "ligature" Shavian letters, we don't want to rely on them for the system to work. If we do, we would be totally dependent on just a few font options, which is not practical for real world use.

<!-- 
| Lexical Set | Rune | Stress |
| --- | --- | --- |
| happY | ᛡ | unstressed |
| KIT | ᛁ | stressed or unstressed | 
| FLEECE | ᛁᛄ | stressed |
| NEAR | ᛁᛁ | mostly stressed |
| commA | ᛟ | unstressed |
| lettER | ᛟᚱ | unstressed |
| NURSE | ᛟᛟᚱ | stressed |
| GOAT | ᛟᚹ | mostly stressed |
| STRUT | ᚢ | stressed |
| DRESS | ᛖ | stressed or unstressed |
| FACE | ᛖᛄ | mostly stressed |
| SQUARE | ᛖᛖᚱ | mostly stressed |
| TRAP | ᚫ | stressed or unstressed |
| PALM | ᚫᚫ | stressed |
| START | ᚫᚫᚱ | stressed or unstressed |
| PRICE | ᚫᛄ | mostly stressed |
| MOUTH | ᚫᚹ | mostly stressed |
| FOOT | ᚣ | stressed or unstressed |
| CURE | ᚣᚣᚱ | stressed or unstressed |
| GOOSE | ᚣᚹ | stressed or unstressed |
| LOT | ᚩ | stressed |
| THOUGHT | ᚩᚩ | stressed |
| NORTH / FORCE | ᚩᚱ | stressed or unstressed |
| CHOICE | ᚩᛄ | mostly stressed |



| juː | jʉ́w | 𐑿 | ᛄᚣᚹ |

| Strong Latin | Weak Latin | Strong Rune | Weak Rune |
| --- | --- | --- | --- |
| eɪ | æ | ᛖᛄ | ᚫ |
| i: | e | ᛁᛄ | ᛖ |
| aɪ | ɪ | ᚫᛄ | ᛁ |
| əʊ | ɒ | ᚢᚹ | ᚩ |
| aʊ | ʌ | ᚫᚹ | ᚢ |
| eɪ | ə | ᚢ | ᛟ |
| i: | ə | ᛁ | ᛟ |
| aɪ | ə | ᛖ | ᛟ |
| əʊ | ə | ᚫ | ᛟ |
| aʊ | ə | ᚪ | ᛟ |
-->

## Differences from ReadLex

### happY vowel

Use the happY rune ᛄ where Shavian would have a trailing 𐑦.

### Syllabic consonants

Often times, you can write just ᛚ, ᛗ, or ᚾ where you see 𐑩𐑤, 𐑩𐑯, or 𐑩𐑥.

In most places you see **𐑩𐑤**, it is because there is a glide right before it. We write the glides, so we don't need to explicitly include the schwas. Only write ᛟᚱ if it represents the suffix -er, or similar.

In many (not all) places where you see **𐑩𐑯** or **𐑩𐑥**, you can just right the ᛗ or ᚾ directly without the schwa needed.

When in doubt, consider the derivatives. 

For example, consider "Terrible". Can it be spelled ᛏᛖᚱᛟᛒᛚ without a schwa before the L? If we can spell the derivative "Terribly" by just adding the -y on the end, then yes! ᛏᛖᚱᛟᛒᛚᛄ (it works!)

Another example, consider "Imagine". Can it be spelled ᛁᛗᚫᚷᚾ without a schwa before the N? If we can spell the derivative "Imagination" by just adding the -ation on the end, then yes! ᛁᛗᚫᚷᚾᛖᛡᛋᚳᚾ. It fails because the syllable boundaries break. It needs to be ᛁᛗᚫᚷᛟᚾᛖᛡᛋᚳᚾ for it to sound right, and thus the base word should be ᛁᛗᚫᚷᛟᚾ.

### Shortcut words

| Latin | Shavian | Runes | Bindrune / Shortcut rune |
| --- | --- | --- |
| the | 𐑞 | ᚦ |
| to | 𐑑 | ᛏ |
| and | 𐑯 | ᚾ |
| for | 𐑓 | ᚠᚱ |
| of | 𐑝 | ᚠ | ![ff bindrune](/assets/images/ff-bindrune.png) |

# Choices

## ᚢ for STRUT

STRUT originally came from the "short u" sound. Because of this, it's appropriate to think that if runes had continued in use, people would have eventually started to pronounce ᚢ as a STRUT.

Why not have the STRUT phoneme be represented by a short PALM letter? While STRUT and PALM can be understood as some kind of pair from a purely objective standpoint, they don't seem related from the subjective English standpoint (which is what we are concerned with). STRUT developed from the letter "u"  and thus remains quite psychologically distinct from "a" sounds for native speakers, despite some closeness in objective sound.

> The STRUT–PALM merger is a merger of /ʌ/ and /ɑː/ that occurs in Black South African English and commonly also in non-native speech.

> A three-way merger of /æ/, /ʌ/ and /ɑː/ is a common pronunciation error among L2 speakers of English whose native language is Italian, Spanish and Catalan.[35][36]

https://en.wikipedia.org/wiki/Pronunciation_of_English_⟨a⟩#TRAP–STRUT_merger

> Interestingly, as with the comment, when /ʌ/ is compared with phonetically similar vowels from different language systems where the possibility of interference is so low as to be negligible, e.g. Russian's [ɐ]/[ʌ] or Korean's [ʌ]/[ɘ], the native language transfer mapped it to a different vowel completely, Northern English's /a/. This shows the difference between phonemic and phonetic similarity very clearly: it is very likely that your familiarity with written English and the close affinity of Northern and Southern English that you associate the sound of [ʌ] with /ʊ/ at all; otherwise you associate it with /a/.

https://linguistics.stackexchange.com/a/7105

One point of this spelling system is that we want common mergers that occur among *native* English speakers to *look* similar (FOOT and STRUT merger, for example). But we want mergers that only occur among *non-native* speakers to *not* look similar at all (STRUT and PALM). If we made STRUT look similar to PALM, we would only be doing non-native learners of English a disservice by validating their common confusion between these two phonemes.

| Latin | Runes  |
| --- | --- |
| putt | ᛈᚢᛏ |
| put |  ᛈᚣᛏ  |
| pool | ᛈᚣᚹᛚ |
| pull |  ᛈᚣᛚ |
| boom |ᛒᚣᚹᛗ |
| bum | ᛒᚢᛗ |

For more info on FOOT ᚣ, [see below](#ᚣ-for-foot).

## ᛟ for commA

You can see on the IPA vowel chart that ᛟ was traditionally more fronted than a commA sound typically is. 

![IPA vowel map](/assets/images/runeSchool2IPAmapNoSchwa.png)

But for the purposes of a functional system, we have pushed the acceptable range of ᛟ into ᚢ's territory so that they essentially overlap by a large portion in the middle.

## ᚢᚱ for NURSE

It's true that the original sound of ᛟ is used for the NURSE vowel in some English accents today. 

If we consider that, to a large degree, ᛟ and ᚢ are only distinguished by stress, then this still makes sense for us. ᛟ could still sound like the nucleus of NURSE, but just unstressed. This would be the sound in lettER for many accents.

## ᚩᚹ for GOAT

Because FORCE is very much related to NORTH, it makes sense that the nucleus of FORCE (GOAT) would also be related to the nucleus of NORTH (THOUGHT).

THOUGHT (ᚩᚩ) is to NORTH (ᚩᚩᚱ) as GOAT (ᚩᚹ) is to FORCE (ᚩᚹᚱ)

Since we merge NORTH and FORCE in most English accents, we should have the two nucleuses the same.

There are a number of accents that make GOAT a monophthong like /o:/ as well. In which case having the visual similarity of ᚩᚩ and ᚩᚹ is good. There is also the historic relationship of GOAT ᚩᚹ being the strong form of LOT ᚩ. 

If you have a more british accent with a clear ᛟᚹ type of pronunciation of GOAT, you can think of GOAT/HOLY being ᛟᚹ and GOAL/WHOLLY being ᚩᚹ. In which case we are just merging HOLY into WHOLLY. 

While Dr Lindsey makes many [great points about words like "halloween" and "Iowa" being ᛟᚹ](https://www.englishspeechservices.com/blog/the-spooky-ambiguity-of-halloween/), he also brings up a number of points of ambiguity such as "away" vs "oasis". We can't show stress very effectively with runes and a choice needs to be made on how to represent this phoneme. For the time being, we are just teaching that ᚩᚹ and ᛟᚹ are cousins, but ᛟᚹ doesn't come around very often.

<!--
## ᚢᚹ for GOAT

ethel used to be related to /o:/ in elder futhark, and GOAT is monophthongized to /o:/ so therefore using it for this GOAT set brings it back home.

It's no secret that GOAT can have a wide range of starting points. But when we consider the possible range of pronunciations for STRUT 

![possible pronunciations for STRUT](https://ecampusontario.pressbooks.pub/app/uploads/sites/1860/2022/05/STRUT_Lexical_Set_2.png)

and the possible range of starting points for GOAT, 

![possible pronunciations for GOAT](https://ecampusontario.pressbooks.pub/app/uploads/sites/1860/2022/05/GOAT_Lexical_Set_2.png)

they are a very good match.

It's true that when GOAT is monophthongized, it tends to be closer to the THOUGHT vowel. Consider though that many pronunciations of ᚢ (STRUT) are just unrounded versions of THOUGHT. So it's not a difficult stretch to say that ᚢ + ᚹ together would make such a sound. The lips round during the off-glide anyway.

There are also some pronunciations of GOAT that involve a FOOT or GOOSE sound. ᚢ being the cousin of ᚣ makes perfect sense for this (more on ᚣ below).

The hull-hole merger feels right at home with this orthography as well. 

ᚢ is just the best middle-ground between the RP style schwa (ᛟ for us) starting point and the GA style ᚩ.

ᚩᚹ will remain a valid orthography for the GOAL lexical set; for when people want to be exact. People may choose to write names with this phoneme, for example. But for the most part, we will recommend that GOAL is subsumed into the GOAT set with ᚢᚹ.

ᚢ also just so happens to not have a lot going on in this system, so this makes the rune a bit more commonplace.
 -->

## ᚣ for FOOT

This rune visually looks like ᛁ inside of ᚢ and would thus be appropriate for any of the sounds between /i/ and /u/ on the IPA sound chart.

The ᚣ rune most likely had a /y:/ sound. It's hard to find a modern day correlate to this sound. But let's look at the data:

| Sound similar to /y/ | Dialects using it for FOOT | Dialects using it for GOOSE |
| --- | --- | --- |
| [[y]](https://en.wikipedia.org/wiki/Close_front_rounded_vowel#Occurrence) | 0 | 4 |
| [[ʉ]](https://en.wikipedia.org/wiki/Close_central_rounded_vowel#Occurrence) | 5 | 6 |
| [[ɨ]](https://en.wikipedia.org/wiki/Close_central_unrounded_vowel#Occurrence) | 2 | 1 |
| [[ʏ]](https://en.wikipedia.org/wiki/Near-close_near-front_rounded_vowel#Occurrence) | 4 | 2 |

So out of the similar sounds, 12 dialects are using it for the GOOSE phoneme and 11 are using it for the FOOT phoneme. It's almost equal! So here are our options:

| Option | STRUT | FOOT | GOOSE |
| --- | --- | --- | --- |
| 1 | ᚢ | ᚢᚢ | ᚢᚹ | 
| 2 | ᚢ | ᚢᚢ | ᚣ | 
| 3 | ᚢ | ᚣ | ᚢᚹ | 
| 4 | ᚢ | ᚣ | ᚣᚹ | 

Another option entirely would be to use ᚣ as a rune that represents /ju:/ like in the word "new". The downside of this is that the "yod" is coalesced to the consonant *before* and **not** to the vowel /u:/. So if the yod is written at all, it would make more sense to be thought of as belonging with the previous consonant, not combined with /u:/.

Option 4 is the best because of the STRUT-FOOT (hull-pull) merger and the FOOT-GOOSE merger. *Visually* STRUT and FOOT look similar and *also* FOOT and GOOSE look similar. So FOOT is the meeting point of the two. Also, STRUT is a more open sound than FOOT on the IPA vowel chart and ᚢ looks more visually open than ᚣ.

## ᛇ for FLEECE

Previously, ᛇ was used for "rad*io*" and "g*eo*graphy" as well as the consonant sound in "lo*ch*". We are keeping the consonant sound the same. However, the vowel sound for this rune was more likely [ji(ː)] or [i(ː)j]. We are representing the FLEECE phoneme as /ij/ and as such, this is the perfect shortcut rune for that sound.

Users may represent FLEECE as either ᛁᛡ or ᛇ.

## ᛄ for happY vowel

"[happY can be associated with either fleece, kit, or face, with vowel qualities in the range of /i ~ ɪ ~ e ~ ɛ/](https://ecampusontario.pressbooks.pub/lexicalsets/chapter/25-happy-lexical-set/)". If anyone has used Shavian before, you know the pain of not having a letter just for this happY phoneme.

Previously, the ᛁ rune represented both KIT and FLEECE and therefore if it was on the end of a word, it could be whatever you wanted it to be. The one issue that would occur from this is the famous confusion of "candied" and "candide".

Now, we have different runes for both KIT and FLEECE. So the happY vowel is now represented with ᛄ. 

ᛄ and ᛡ are famously controversial. Many believe that they are two different styles for the same rune. But the fact is that multiple manuscripts contain both of these runes and they even have different names. That would not be the case if they were just stylistic variants of the same rune.

ᛡ was called "Īor", (probably) meaning "eel". ᛄ was called "Gēr", meaning "year". 

Realistically, both of these runes could be a /j/ sound. But it's postulated that ᛡ specifically had a /jo/ sound. Therefore, it seems more appropriate for making diphthongs like /ej/, /aj/, /oj/, etc. 

So what do we do with ᛄ? Well, just like the use of the letter "y" in latin English, it can have a use as the happY phoneme.

| Latin       |  Runes |
| -------- |  ------ |
| Kale        |  ᛣᛖᛡᛚ      |
| Kyle        |  ᛣᚫᛡᛚ      |
| Coil        |  ᛣᚩᛡᛚ      |
| Geography   |  ᚷᛄᚩᚸᚱᛟᚠᛄ  |
| Radio       | ᚱᛖᛡᛞᛄᚩᚹ   |
| Kitty       |  ᛣᛁᛏᛄ      |
| Create      | ᚳᚱᛄᛖᛡᛏ    |
| Easily (1)  |  ᛁᛡᛉᛁᛚᛄ     |
| Easily (2)  |  ᛇᛉᛁᛚᛄ    |
| Yield (1)   | ᛡᛁᛡᛚᛞ     |
| Yield (2)   |  ᛡᛇᛚᛞ      |
| Reality   |  ᚱᛄᚫᛚᛁᛏᛄ      |
| Candied     |  ᛣᚫᚾᛞᛄᛞ    |
| Candidly    |  ᛣᚫᚾᛞᛁᛞᛚᛄ  |
| Candide (1) |  ᛣᚫᚾᛞᛁᛡᛞ    |
| Candide (2) |  ᛣᚫᚾᛞᛇᛞ   |

Ultimately, if a user uses just one rune for both happY and /j/, it's not the end of the world. But offering this distinction should aid in clarity.

This solution also keeps ᛡ more common than ᛄ which is true to the Anglo-Saxon corpus as well.

## ᚪ as a shortcut for ᚫᚫ

Traditionally, you will often see things like /æɪ/ in that old dictionaries for the pronunciation of PRICE. This is because historically TRAP has always been thought of as a short PALM. Think of how a boston person says “spa”. They say it with a long TRAP sound. Think of how Irish people say START. They say it very obviously like ᛋᛏᚫᚫᚱᛏ (a long TRAP sound).

And then we consider the internal logic of the doubled runes. Doubled vowels bring the sound a bit closer to the center of the IPA chart. Doubling ash brings it more in the middle where SPA is.

Also consider the variability of words in the BATH lexical set. Some go to TRAP and some go to PALM. This is to say that some say the words with a long TRAP sound (PALM) and some with a regular TRAP sound.

And consider the design of the look of the runes. It makes sense that ᚫ and ᚩ are the primary ones. Both fully realized runes. Then ak develops as a sort of in between rune ᚪ.

And finally, consider that this is better for crosswords and other word games. More utility with less letters (if you exclude shortcut runes).

In a hundred years if there is a meaningful split within PALM or TRAP, that will be workable with this system. I doubt that such a thing would occur within 500 years at least, but if it happens, we would just say “ᚪ rune grew up and earned its own row in the table!”

# Questions?

If you have further questions, please see the [FAQ](/rune-school-spelling-system-faq) post.
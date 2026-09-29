# kuvinte-wordlist

The derived Romanian wordlist used by the **Kuvinte** word game, published here under the
**Mozilla Public License 1.1** — the licence leg its upstream dictionary is offered under.

This repository exists to satisfy that licence: hunspell-ro is distributed under an
MPL-1.1 leg, and a derivative of MPL-licensed source must be made available under the same
terms. `wordlist-published.mpl.txt` is that derivative.

## What is in here

| file | what it is |
|---|---|
| [`wordlist-published.mpl.txt`](wordlist-published.mpl.txt) | 1,361,274 Romanian word forms, one per line, sorted. Carries the filled-in MPL 1.1 Exhibit A notice in its own header. |
| [`LICENSE`](LICENSE) | The full text of the Mozilla Public License 1.1. |

## Provenance

**Original Code:** the Romanian Hunspell dictionary — "hunspell-ro" / "rospell",
`ro_RO.dic` + `ro_RO.aff`, **version 3.3.10** (released 2013-11-12),
<http://rospell.sourceforge.net>.

- Initial Developer: the Rospell Team. Portions created by the Rospell Team are
  Copyright (C) 2005–2013 Rospell Team. All Rights Reserved.
- Contributors, per the pinned distribution's own README: Lucian Constantin, Andrei Cipu,
  Sorin Sbarnea, Alexandru Szasz, Ionut Paduraru, Adrian Stoica, Nicu Buculei, Catalin
  Francu, Ionel Mugurel Ciobica, Mihai Budiu.
- Upstream is **tri-licensed** GPL-2.0 / LGPL-2.1 / MPL-1.1. The **MPL-1.1 leg is the one
  elected here**, and it is the leg this derivative is published under.

The exact upstream bytes this was built from are pinned by sha256, never taken from a mirror:

```
ro_RO.3.3.10.zip  7f128d64ea06c9e6711c30b118c0afeefb014d8f33c92daccdf455aba2d04519
ro_RO.dic         c26a9356f598a0ae89e7be650f6bdd9ba70acce66b41d7ab14c0c68639b6ed33   (181,357 entries)
ro_RO.aff         0c83a02f0ac5202c068e60e1aef5ce99e13d7f6c92ae8e68ca8b9e06829edfd1
```

## How the 181,357 dictionary entries became 1,361,274 forms

1. **Affix expansion.** Every `.dic` stem is expanded against its `.aff` affix flags, so
   inflected forms are present as playable words, not only their lemmas.
2. **Structural filtering.** Forms that cannot be traced on a 4x4 letter grid are dropped,
   including every form longer than 16 letters.
3. **Diacritic folding.** Forms that differ only in diacritics are folded into one class, with
   ș/ț always the comma-below letters (U+0219 / U+021B), never the cedilla ones.
4. **One display spelling per class.** Chosen by how often each spelling appears in the
   [FrequencyWords](https://github.com/hermitdave/FrequencyWords) Romanian list (Hermit Dave),
   with a few fixed by hand. Every form here is hunspell-ro's own.

## Caveats for anyone reusing this

- **It is a game's wordlist, not a reference dictionary.** The cuts above serve a 4x4 grid;
  they are not lexicographic judgments.
- **It includes rare and vulgar words.** They are real dictionary words; the game handles them
  when it shows words, not by deleting them from the list.
- **It is a snapshot.** It changes only when the Kuvinte project regenerates it.

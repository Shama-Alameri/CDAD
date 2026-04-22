---
title: "A2: Two Tools, One Corpus"
authors: "Shama & Mhara"
layout: single
date: 2026-04-22

categories:
  - posts
  - responses
tags:
  - Stylo
  - TF-IDF
  - Assignment 

---
****IN Progress****
## Introduction

Our assignment was essentially a question dressed up as a project: if you hand the same pile of books to two different computational tools, do they see the same library, or two different ones? The pile in question is a small but surprisingly varied corpus of 18 science fiction and speculative fiction texts pulled from Project Gutenberg, and the two tools are a matched pair of opposites.

- **Stylo** (an R package) obsesses over the most frequent words in a text, the quiet scaffolding of *the*, *and*, *of*, *was*, and tries to work out who wrote what from those alone.
- **TF-IDF** does the mirror image. It pushes those common words aside and spotlights whatever vocabulary is *peculiar* to each text.

The cliche is that Stylo catches authorship and TF-IDF catches topic. We wanted to see whether that holds up on a corpus of pulp space opera, Martian princesses, and, for some reason, a non fiction essay collection by H.G. Wells. Hanging over all of it is Ted Underwood's warning in "The Risks of Distant Reading" that a model is not a tool you plug in, it is "a new way of representing and interpreting the world." If he is right, Stylo and TF-IDF should disagree in ways that matter.

## A quick note on the corpus

The 18 texts lean heavily into American pulp sci fi from the 1940s through the early 1960s, with one older British voice for contrast. All author notes below are drawn from Wikipedia,  and summed up into bullet points with the help of an LLM (Claude)

**Leigh Brackett** (3 novels, including *Enchantress of Venus* and *The Black Amazon of Mars*)

- Published 17 stories in *Planet Stories*, the magazine she is most identified with alongside Ray Bradbury
- Her planetary romances lean on a recurring decadent, dying Mars and a wet, jungle Venus
- A central theme is the clash of planetary civilisations, often used as a critique of colonialism
- Also co wrote the screenplay for *The Empire Strikes Back*

**Philip K. Dick** (3 stories, all from 1953)

- Born 1928, died 1982; began publishing science fiction in 1952 at age 23
- Wrote 45 novels and around 121 short stories over his career
- Known for alternate realities, altered states, authoritarian governments, and slippery questions of identity
- Later adapted into *Blade Runner*, *Total Recall*, and *Minority Report*

**Andre Norton** (3 novels)

- Real name Alice Mary Norton; "Andre" was a career decision in a male dominated genre
- Published more than 300 titles across 70 years of writing
- Named an SFWA Grand Master in 1984 and won the World Fantasy Lifetime Achievement Award in 1998
- The Andre Norton Award for YA science fiction and fantasy was created in her honour in 2005

**H.G. Wells** (3 works)

- English, 1866 to 1946, sometimes called the "father of science fiction"
- Produced *The Time Machine*, *Moreau*, *War of the Worlds*, and others in a famous six year burst from 1895 to 1901
- Critic John Clute calls him "the most important writer the genre has yet seen"
- Also wrote widely in non fiction: social commentary, politics, popular science, biography, which is the tradition *The Salvaging of Civilization* sits in rather than his fiction

**Marion Zimmer Bradley** (3 works)

- Started writing at 17; holds a BA from Hardin Simmons University
- First *Darkover* novel, *The Planet Savers*, published in 1958 in *Amazing Stories*
- Co founded the Society for Creative Anachronism in 1966
- Often credited with bringing a female perspective into sword and sorcery fiction at a time when the genre ignored one

**Henry Kuttner** (3 stories, including *The Black Kiss*, co written with Robert Bloch)

- Born 1915, died 1958; first sale was "The Graveyard Rats" to *Weird Tales* in 1936
- Married C.L. Moore in 1940, and most of his 1940 to 1958 output was co written with her
- Shared multiple pseudonyms with Moore, most famously "Lewis Padgett"
- Ray Bradbury called him a "neglected master" and a "pomegranate writer, popping with seeds, full of ideas"

On paper the corpus spans 65 years. In practice almost everything clusters into a mid century American magazine band, with Wells sitting on the edge like a Victorian uncle at a pulp convention.

## Tool 1: Stylometry with Stylo

### What it does

Stylo's premise is a little unnerving: authorship shows up best not in a text's flashy vocabulary but in its plumbing. Writers are weirdly consistent in how often they use tiny connective words like *the*, *and*, *of*, *was*, *that*, *which*, and Stylo does basically nothing but count those rates. It runs a distance metric (**Classic Delta**) across the corpus and draws either a **Cluster Analysis (CA)** dendrogram or a **Bootstrap Consensus Tree (BCT)** that averages multiple runs. We ran CA at 100, 300, and 500 most frequent words (MFW), plus a BCT spanning 100 to 500.

### Results

At **100 MFW**, the tree is almost suspiciously clean:

- Dick's three stories cluster together at the top.
- Norton's three novels cluster together at the bottom.
- Wells's two fiction novels pair off in their own branch.
- Brackett and Kuttner tangle in the middle.
- Zimmer Bradley's tiny *Jackie Sees a Star* (only 10KB) floats near Dick, separated from her own novels.
- *The Salvaging of Civilization* falls off the bottom, exiled on its own branch.

![Stylo CA at 100 MFW](./assets/images/stylo-ca-100mfw.png)

Push the MFW count up, though, and things loosen. At **300** and especially **500 MFW**, Brackett's *The Blue Behemoth* drifts off to sit next to Kuttner's *The Ego Machine*, which itself keeps creeping towards Zimmer Bradley's novels, as if Kuttner were quietly trying to colonise half the tree. Dick and Norton, by contrast, held their internal shape perfectly, each cluster stayed as tightly packed as it was at 100 MFW, but the two clusters swapped positions in the tree. Norton migrated up to where Dick had been, and Dick slid down to where Norton had been. They did not break, they just traded seats.

![Stylo CA at 500 MFW](./assets/images/stylo-ca-500mfw.png)

The BCT (below) smooths those shifts into one radial picture. Dick and Norton still read as stable islands, Brackett and Kuttner share a neighbourhood rather than occupying separate ones, Wells's novels drift towards *The Black Kiss*, and *The Salvaging of Civilization*, bafflingly, ends up near Norton.

![Stylo BCT, 100 to 500 MFW](./assets/images/stylo-bct-delta.png)

### Analysis

Three things jumped out.

**1. Stylo mostly delivers what the textbook promises.** Dick, Norton, and the Wells fiction novels clustered neatly by author, with the cleanest signal at low MFW counts, which is exactly where function words dominate. The unconscious rhythms of *the* and *and* really are a better fingerprint than topic vocabulary. The genuinely interesting thing about the Dick and Norton seat swap is what did *not* happen around it: the two clusters flipped positions in the tree, but internally they held their shape perfectly from 100 MFW through 500 MFW, even as the vocabulary pool around them quintupled. That resilience is arguably a bigger finding than the tidiness at 100 MFW alone, because it shows the author level signal for these two writers is not a fluke of parameter choice. It survives being drowned in extra words.

**2. The method is not magic.** Length and genre smuggle themselves into the results. *Jackie Sees a Star* is too short for reliable frequency counts, so it drifts wherever the noise pushes it. *The Salvaging of Civilization* is non fiction, so it refuses to cluster with pulp narratives under any parameters we tried. Neither case is Stylo failing. Both are the tool honestly reporting that a dendrogram is not reading books, it is counting *the*s and *and*s.

**3. The Brackett and Kuttner blur is the most interesting finding.** Both ran their careers through the same pulp magazine era, Brackett centred on *Planet Stories* and Kuttner publishing from 1936 through 1958 out of *Weird Tales*. Both even share a Ray Bradbury connection: Brackett as the other writer most identified with *Planet Stories*, and Kuttner as a writer Bradbury personally championed as a "neglected master." If Stylo were a flawless authorship detector, it would prise them apart. The fact that it cannot is probably the more honest answer: a shared commercial tradition and a shared audience can genuinely produce a shared stylistic footprint, which is a claim we could not have made from reading alone.

By the end of the Stylo pass, we have a reasonable map of **who writes like whom**. The follow up question, which we take to TF-IDF next, is whether that map of *style* has anything at all to do with a map of *content*. The suspicion, going in, is that it will not.

*(BP2, Tool 2, BP3 to follow.)*

## Sources for corpus info (all Wikipedia)

- [Leigh Brackett (Wikipedia)](https://en.wikipedia.org/wiki/Leigh_Brackett)
- [Philip K. Dick (Wikipedia)](https://en.wikipedia.org/wiki/Philip_K._Dick)
- [Andre Norton (Wikipedia)](https://en.wikipedia.org/wiki/Andre_Norton)
- [H. G. Wells (Wikipedia)](https://en.wikipedia.org/wiki/H._G._Wells)
- [Marion Zimmer Bradley (Wikipedia)](https://en.wikipedia.org/wiki/Marion_Zimmer_Bradley)
- [Henry Kuttner (Wikipedia)](https://en.wikipedia.org/wiki/Henry_Kuttner)
- [Planet Stories (Wikipedia)](https://en.wikipedia.org/wiki/Planet_Stories)

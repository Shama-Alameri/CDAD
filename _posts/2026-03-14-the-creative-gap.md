---
title: "R1: The Creative Gap"
layout: single
date: 2026-03-14
categories:
  - posts
  - responses
tags:
  - Voyant
  - RMarkdown
  - Response
---
Through our very first attempts at using tools for distant reading, I created several visuals to understand Post-Colonial South Asian literature through my own interpretations as someone who has never read books that fall within this category. Many visuals had to be scraped away, as I could not possibly use them to connect to my developing theories and understanding. This made me wonder: as humans, when we see something with no context, we tend to rely heavily on our creativity to arrive at conclusions that satisfy us. Does AI do the same? I wanted to explore this question by using Gemini to see what might happen when given the same lack of context, without any prior prompt hinting that these visuals came from a corpus of Post-Colonial South Asian literature.

<figure>
  <img src="{{ '/assets/images/Jojo.jpg' | relative_url }}"
       alt="Compact word‑cloud">
  <figcaption>Figure 1: The Heat Map</figcaption>
</figure>

I wanted to start off heavy with the heatmap (Figure 1) I generated through RMarkdown including all the books. I asked Google's Gemini to analyze it and look for any patterns that could create connecting theories and themes from the context in the image. Through this prompt it first tried to connect the rows (authors) to see if they had any similarities in nationality, and attempted to cluster them if they shared patterns. Henty and Candler were placed in the first group, both Asian authors in the second group, and Kipling was labeled the "outlier."

After grouping the rows, it moved to the columns. Gemini identified the left side as connecting to themes of "Identity and Ideals," the middle columns focusing on "Conflict and Loyalty," and the right side representing the "Universal Human Condition." It then began connecting both authors and thematic words into broader interpretive theories, framing the Indian authors as writing from a more internal, philosophical perspective, drawing heavily on words like **soul**, **truth**, and **life**, while the British authors leaned toward an external, action-driven lens anchored by **man**, **gun**, and **land**.

What struck me most was that Gemini arrived at a distinctly colonial reading of the data purely through pattern recognition, without ever being told these texts had anything to do with colonialism. Much like a human squinting at an unfamiliar image and reaching for the nearest familiar framework, Gemini appeared to fill the gap of missing context with its own interpretive logic. It similarly latched onto Chatterji's notably high frequency of the word **woman**, connecting it to the concept of nationhood embodied through a maternal figure, again a culturally specific conclusion drawn from nothing more than a number on a grid. Whether this reflects genuine analytical depth or simply a confident projection, much like we ourselves tend to do, is precisely the kind of question this experiment raises.

Perhaps most tellingly, Gemini also noted the near-absence of explicitly political words like **nation** and **violence**, reading this silence as meaningful rather than incidental. In doing so, it was not just describing the data. It was storytelling. And that, arguably, is a very human thing to do.

<figure>
  <img src="{{ '/assets/images/Chocho.jpg' | relative_url }}"
       alt="Compact word‑cloud">
  <figcaption>Figure 1: The Word Frequency Chart</figcaption>
</figure>

After the interesting result I received from Figure 1, I wanted to test one of the many charts I got through VoyantTools. As seen in Figure 2, this chart lacks the full context of what the corpus might be hinting at, with no mentions of authors or titles, which honestly made me even more excited to see what result might come out of it.

Gemini's response was immediate and confident. Without hesitation, it anchored its entire interpretation around the idea of a military conflict set in South Asia, largely because of the word **india** appearing twice and **sandip** appearing four times. It grouped words like **major**, **guns**, and **enemy** into what it called an "operational cluster," building a narrative of organized conflict around them. What is fascinating here is how quickly it committed to a singular, coherent story. Rather than acknowledging ambiguity, it moved decisively toward the most dramatically satisfying explanation the data could offer.

Interestingly, Gemini also picked up on the quieter, more domestic words like **house**, **hand**, and **mother**, and rather than treating them as contradictions to its military theory, it wove them in as emotional subtext, framing them as evidence of "human impact amidst conflict." This mirrors something we often do ourselves: when we have already decided on a narrative, we tend to absorb contradicting details into it rather than letting them challenge the whole picture.

What this experiment ultimately revealed is a crucial difference hiding beneath the surface similarity. Yes, Gemini produced theories, made connections, and even read silences as meaningful, but it never once hesitated. There was no moment of genuine uncertainty, no scrapped interpretation, no visual thrown away because it did not fit. I had plenty of those. Literary scholar Ted Underwood warns against exactly what I was witnessing, cautioning that the belief that delegating observation to a machine somehow increases "the objectivity of results" is a fantasy rather than a reality (Page 157). Gemini's confidence was not objectivity at all. It was pattern-matching dressed as insight, a performance of certainty that had no need for the doubt that shaped my own process. And maybe that is the real distinction: humans create meaning through doubt, through dead ends, and through the uncomfortable feeling of not knowing. Gemini simply skips that part, and in doing so, produces something that looks like insight, but perhaps lacks the struggle that makes insight meaningful.
:)
## References

- Underwood. *Distant Horizon*. [Distant Reading](https://newbooksnetwork.com/distant-reading) - New Books Network

### Tools & Resources

- [Voyant Tools](https://voyant-tools.org/)
- [RMarkdown Documentation](https://posit.cloud.com/)
- [Gemini (2026). Gemini AI](https://gemini.google.com/)

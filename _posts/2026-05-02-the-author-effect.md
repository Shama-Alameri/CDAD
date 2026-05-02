---
title: "R2: The Author Effect"
layout: single
date: 2026-03-14
categories:
  - posts
  - responses
tags:
  - Stylo
  - TF-IDF
  - Response
---
While working through Assignment 2, I started to notice that the same figure could read very differently depending on what was already in my head when I looked at it. A dendrogram that felt like a clear authorship signal one afternoon could feel like a noise-from-length artefact the next morning, even though nothing on the page had changed. What made the slipperiness harder to ignore was watching my assignment partner come back with a noticeably different account of the same images, same data, same plots, just a different sense of what the figures were actually doing. The figure was fixed. The reading was not. This made me wonder how an AI would handle the same kind of slipperiness, especially on a corpus I had already spent days living inside. Would Gemini and I look at the same image and see the same thing, or would the figure turn into something different the moment a different reader picked it up? For this round of the experiment I went back to Gemini, but this time I had my own analysis of the same images sitting next to its. I deliberately picked two figures from Assignment 2 that share the same MFW setting (300), one from Stylo and one from TF-IDF, so the only thing really changing between the two reads was the reader.

<figure>
  <img src="{{ '/assets/images/stylo-ca-300mfw.jpg' | relative_url }}"
       alt="Stylo CA at 500 MFW">
  <figcaption>Figure 1: Stylo CA at 500 MFW</figcaption>
</figure>

I started with the Stylo cluster analysis dendrogram. Gemini's first move was to sort the figure into a sequence of confidently named, theme-anchored clusters. The green Dick branch, for example, became a "High-Concept Cluster" tied to "Cold War anxieties" and "the nature of humanity"; other groupings were given similar treatment, each one labelled with a tidy thematic phrase that read more like a back-of-book blurb than an inference drawn from the figure itself. Wells was split between his fiction novels and the *Salvaging of Civilization* outlier, which was correctly identified as a work of non-fiction political theory. On the surface, the structural reading aligned almost exactly with mine. Same clusters, same outliers, same blurry middle.

What was different was where Gemini chose to sit. My own analysis tried to stay inside what Stylo can actually claim: that function-word frequencies produce the patterns, that length and genre leak in as noise, that the Brackett-Kuttner blur is the most informative signal because it points at a shared pulp ecosystem rather than at either author specifically. Gemini went the other direction, framing the figure through what was already known about the writers attached to it. It even introduced a "Gendered Stylometry" theory, suggesting that the lower half of the diagram was a "loose grouping of female authors" with "shared stylistic conventions." That reading is not in the data. It is in the surrounding cultural narrative. Stylo measured *the*, *and*, *of*, and *was*, not gender, and the placement Gemini was reading as a feminine cluster includes Norton, who only became Andre because the genre would not publish her under Alice. The visual could not have told Gemini that. Gemini's prior knowledge could, and that knowledge was bleeding into the reading anyway.

<figure>
  <img src="{{ '/assets/images/MFW300.jpg' | relative_url }}"
       alt="Stylo BCT, 100 to 500 MFW">
  <figcaption>Figure 2: TF-IDF, MFW: 300 </figcaption>
</figure>

The TF-IDF scatter pulled an even bolder version of the same move. Gemini built out three full named cluster-theories and then layered two cross-cutting axes on top, a "Spectrum of Science vs. Fantasy" and a "Macro vs. Micro Philosophical Divide." Each theory came with confident, almost authoritative phrasing. Wells, for instance, was framed under an "Originator Hypothesis" that "stands alone because his work defines the core archetypes," while Dick's outliers were said to be "famously about reality distortion, paranoia, and internal psychological landscapes." The language felt less like a reading of a scatter plot and more like jacket copy, with the figure providing the locations and Gemini providing everything else.

Reading this beside my own write-up was strange because the underlying observations overlapped without the reasoning ever overlapping. I had reached the same finding about Wells, that the two tools agreeing on his fiction is the strongest convergence in the project, but I had reached it as a careful comparison between methods. Gemini reached it as authorial destiny. I had treated *Jackie Sees a Star*'s outlier position as a length artefact, since the file is only ten kilobytes and the method genuinely struggles with that little text. Gemini did not mention length at all and read the position purely as semantic distance. I had treated the Brackett-Kuttner overlap as a methodological insight, evidence that a shared magazine tradition shapes vocabulary in ways individual style cannot fully separate. Gemini absorbed that overlap into the broader pulp synergy theme without ever asking whether the visualisation could actually distinguish "shared genre" from "shared style," which is the exact question I had spent my own analysis trying to hold open.

What this round of the experiment ultimately showed is something a little different from the post-colonial one. There, the model invented a frame because nothing told it not to. Here, it reached past the figure entirely. Each cluster Gemini named was less a pattern observed in the data than a place to anchor something it already had a story about, and the named theories that came back attached to those clusters read more like canned descriptions of the authors themselves than like analyses of the figure they were supposedly drawn from. The visualisation did not really constrain the readings. It gave Gemini somewhere to hang prior associations and call them findings. Underwood's caution that delegating observation to a machine does not increase "the objectivity of results" (Page 157) felt even more pointed in this version, because the figure was barely even doing the observing. The model already had the story, and the figure was just an excuse to tell it. The clusters Gemini and I named overlapped almost completely. The reasoning underneath did not, and that gap, between letting the tool do the work and letting prior knowledge do it for you, is what this experiment turned out to be about.

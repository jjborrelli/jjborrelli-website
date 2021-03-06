---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Selection on Stability"
summary: "Identifying the potential for systemic selection against unstable structures."
authors: []
tags: [Food Web, Stability]
categories: []
date: 2018-06-15T07:47:41-04:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

Selection on stability is the idea that there are certain patterns in natural communities that may be observed over long timescales simply because they are more likely to be stable. To give you an overview of the theoretical framework I am using,  I will start with a simple example from outside of ecology.

In the past there were numerous engineers coming up with designs for “flying devices.” Most of these designs failed, some more spectacularly than others, but some were able to allow for sustained flight (like the Wright brother’s aircraft). Those designs that worked, were carried forward and persisted through time, and now what we see in the air today are those stable designs. We can formalize this into the framework for stability selection. There must be some pattern generating mechanism, in the case of the example it was the creation of airplane designs. Patterns that are stable are able to persist through time and become what we observe over long timescales. Of course, you did not come here to hear me talk about planes.

Moving away from such artificial examples into the realm of ecology, I want to talk about food webs (honestly what else was I going to talk about). Food webs are a way for us to visualize complex feeding relationships in a community. Species are the nodes of the network, while the links are feeding relationships. What may be most fascinating about them is that there are so many similarities in the structure of food webs, regardless of the type of community they describe. To try and identify what makes food webs so similar in structure I decided to deconstruct them and examine their basic building blocks. The question is then, how should I break these webs down? Do I go down to the single species? Two? Ten?

It turns out that 3 species configurations are the most dynamically interesting building blocks, while still being small enough to be computationally tractable. There are a relatively small number of possibilities, these are the only 13 ways to put together 3 species compared to 199 for 4 species and over 1000 for 5 species configurations. Note that in these diagrams arrows point in the direction of energy flow. There are also some well-studied community configurations here as well, including the tritrophic chain (where a basal species is eaten by an intermediate predator, which is then eaten by a top predator), exploitative competition (two consumers competing for one resource), apparent competition (two resources with a single consumer), and intraguild predation (two consumers on the same resource, but one consumer eats its competitor as well).

The stability selection framework can help us understand what makes the basic building blocks of food webs. Food web structure will be generated by the introduction of new species through invasion and speciation, species loss from extinction, and the altering of interactions through foraging decisions and population dynamics. Given a set of species and their many potential interactions, some configurations will be more stable than others. Those that are more stable should then be the “motifs” or recurrent structural patterns that are observed more often than expected by chance in food webs.

There are two major components that would constitute evidence that stability selection leads to the observed pattern of motifs. (1) That the subgraphs, the 13 three species configurations, are variable in their stability properties, some should be more stable than others, otherwise there would be nothing to select, and (2) that the variability in stability should map to the observed frequency in empirical food webs, the stable subgraphs should be more frequently observed than we would expect by chance. If not, then there would be no reason to suspect a connection between stability and frequency.

But what do I mean by stability? You may remember reading Stuart Pimm’s 1984 paper on the subject during Principles of Ecology, in which he discussed the abundance of definitions of “stability” pervading community ecology. I focus on two distinct but related definitions: eigenvalue or local stability, and sign-stability. When the community is locally stable it will return to equilibrium following a small perturbation. In these first two images, if you make a small push away from the ball’s resting place, it will eventually return to where it was. Sign stability extends the idea of local stability.

It tells us if a matrix will be stable based only on the pattern of signed relationships, which for predator-prey is (+/-). If a community is sign-stable, then no matter what the magnitude of the species interactions are, as long as they are properly signed, the matrix will be locally stable, mathematically meaning that all of the eigenvalues will be negative. However, in order for a configuration to be stable, it must fulfill specific conditions, which are not met by most natural communities. For example, the presence of loops in a food web negates any chance that it will be sign stable.

Stefano Allesina and Mercedes Pascual in 2008 recognized that sign stability does not have to be all or nothing, but there can be degrees of stability in between. Quasi sign-stability can tell us to what extent a configuration is sign-stable. To find it, we can take the sign matrix and fill it with random values and determine whether it is stable. When we repeat this process several thousand times, the proportion of stable randomizations is the degree to which it is sign stable. It follows from the idea that a sign stable configuration is robust to changes in how large an impact species have on one another, so quasi sign stability can tell us how robust is this configuration.

It was fairly simple to generate a sign matrix for each of the thirteen subgraphs, where each link is a (+/-). Here is the sign matrix for the exploitative competition motif, the negatives on the diagonal indicate density dependence. All values were drawn independently and randomly from a uniform distribution. I made the simplifying assumption that the impact of prey consumption on predator population growth was larger than its impact on prey population growth, but my results are robust to changes in that assumption. For each sign matrix, I generated 10,000 randomized versions and then determined whether or not each randomly filled matrix was stable. Quasi sign stability was then found as the proportion of stable matrices.

Three of the subgraphs were always stable, one was stable about 50% of the time, and the rest were rarely stable. When I alter the distributions I used to generate the random matrix, the results are qualitatively similar, and the three stable subgraphs are always the most stable. So the first component of the signature of stability selection is supported, the thirteen configurations have variable stability properties.

The three that are always stable are the tritrophic chain, apparent competition, and exploitative competition. With intraguild predation being the one that is stable 50% of the time. If these subgraphs are also more frequently observed and the others are less common, then we will have the expected signature of stability selection. To determine the frequency of each of these subgraphs I found data for 50 empirically described food webs from several public sources.

The food webs that I am using range from 30 to 250 species and 70 to 4000 links.

The problem with using this variety of webs is that you cannot directly compare the patterns across networks with a different number of species or with a different number of links. For example, one of these networks may have a higher frequency of apparent competition motifs simply because there are more species making up the network and more links connecting them.

The solution then is to use a null model. Here, I used a variation on a swap algorithm to permute the links in each web. Food webs can be represented as binary matrices, where a one indicates that the row species feeds on the column species. To create the null distribution of food webs I shuffled the pattern of ones and zeros in the matrix, essentially swapping links between species. For each of the null webs I determined the frequency of the 13 different subgraphs and used that to generate a z-score for each combination of web and subgraph.

The normalized profile of the subgraph structure of all 50 empirical food webs is fairly interesting. Because these are normalized z-scores, when the box is above the line it means that the subgraph occurs more frequently than expected by chance, and below line is less frequently than expected by chance. Three subgraphs in particular stand out as being noticeably more frequent than we would expect, the tritrophic chain, apparent competition, and exploitative competition. So we have the second component to the signature of stability selection, that the variability in stability should map to the observed frequency.

So do I have proof that stability selection, the preferential loss of unstable configurations, is responsible for the observed patterns in food web structure? No. But the evidence I have shown you is consistent with the hypothesis of stability selection.

But why does stability selection matter? It can be a powerful yet simple tool to help us generate an expectation of what types of patterns should be observed in natural systems. Aside from patterns of motifs in food webs, this framework can be used to explain the shortness of food chains in food webs, where the average trophic position is rarely higher than 5. I have shown in previous work that food webs made of shorter food chains are more likely to be stable then webs constructed with longer chains.

In addition, explorations of predator prey models have suggested that combinations of high attack rates and high handling times lead to increased oscillatory dynamics, leading to an increased risk of extinction during periods of low abundance. Thus based on the framework I have explained here we should expect such high-high combinations to be rare, a prediction that is supported by empirical evidence, seen here for two intertidal whelk predators.
---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Trophic"
summary: "An R package to simulate trophic networks and their dynamics."
authors: []
tags: []
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

*Trophic* is an R package I am working on to compile functions for generating food web structures. It currently has 9 different methods available to generate adjacency matrices. 

I have several goals for this work beyond simply generating food web structures. I hope to implement methods developed by Allesina et al. to determine the likelihood that an observed food web was generated using a specific algorithm. 

I also plan to link this package to models of food web dynamics, in order to make it easier to generate and simulate food webs for testing theory. 
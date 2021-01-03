---
layout: post
title: "Timnit Gebru's Work on Algorithmic Fairness"
date:  2020-12-28 
author: "Lavanya Singh"
presenter: "Lavanya Singh"
categories: [fairness, ML, society]
papers:
- name: "Closing the AI Accountability Gap: Defining an End-to-End Framework for Internal Algorithmic Auditing"
  link: "https://arxiv.org/pdf/2001.00973.pdf"
- name: "Image Counterfactual Sensitivity Analysis for DetectingUnintended Bias"
  link: "https://arxiv.org/pdf/1906.06439.pdf"
---

## Inspiration

As you may have heard, Google recently fired Dr. Timnit Gebru, a leading researcher in AI ethics and the 
founder of Black in AI. Before firing her, Google blocked her from publishing a paper called "On the 
Dangers of Stochastic Parrots: Can Language Models Be Too Big?" You can probably guess what that paper
was about. For more information on the controversy, [see](https://www.vox.com/recode/2020/12/4/22153786/google-timnit-gebru-ethical-ai-jeff-dean-controversy-fired). 

## Papers

Stochastic Parrots hasn't been published yet, so we decided to read some of Dr. Gebru's other work this 
week. ["Closing the AI Accountability Gap: Defining an End-to-End Framework for Internal Algorithmic 
Auditing"](https://arxiv.org/pdf/2001.00973.pdf) describes a procedure for auditing the development of 
AI. ["Image Counterfactual Sensitivity Analysis for DetectingUnintended Bias"](https://arxiv.org/pdf/1906.06439.pdf) 
is more technical, and we spent most of the session discussing it.  

## Discussion

The second paper describes a procedure for detecting bias in a classifier, using the example of a 
smiling face detector. To check for bias, we might ask "Would the prediction change if I was older?" That
might indicate a bias based on age. The authors model that question by generating a version of each 
image that moves either positively or negative along the "attribute vector" for age, producing an older
or younger version of the same image. They then see how the classifier classifies that new generated 
image.

One complication that the paper brings up, and that we had questions about, was the case of correlated
attribute vectors. Age and baldness are correlated, so how can we tell if our classifier is biased
based on age or on baldness? The authors seem to think this is a serious problem, but we thought that 
it might not be such a big issue. After all, a human being that is biased against old people is 
also probably biased against bald people, because the attributes are in fact correlated. 

The authors get around this problem by giving the attribute vectors a "perception score" which is 
created by asking real people to rate whether or not the generated image actually does seem older or
younger. This is tricky: the choice of humans whose perception you use is an important hyperparameter
that could change what kinds of bias go detected or undetected. 

We also wondered whether or not this paper achieves its goal of detected unintended bias. How 
interpretable are the results of this kind of analysis? Does tweaking a generated image actually
tell us anything about bias? It seems like some movements along an attribute vector might not reflect
the real world at all, and the paper does have some pretty unnatural looking images. How can you encode
complex attributes like race in a single attribute vector? We thought that looking at more complex
combinations of attribute vectors might be a basis for future work.

The authors ran their classifier on output images of a GAN. We're sure that there's plenty of work on 
GAN inputs to classifiers that we're unaware of, and we thought that this was an interesting concept.
Do classifiers perform differently on GAN output images and real images? Is this a problem? What are 
the consequnces of using GAN output images to increase diversity in your dataset? 

## Tangents

As always, we went on many tangents during our conversation. Here are a few:
<ul>
<li>Why do so many AI papers automate tasks that humans are really good at, like smiling detection?</li>
<li>Does using AI for science create intellectual and knowledge debt? Like yeah Google solved protein
folding but do we really know how protein folding works? Here's an <a href="https://www.newyorker.com/tech/annals-of-technology/the-hidden-costs-of-automated-thinking)">interesting article</a> on this. </li>
<li>What are everyone's plans for next semester? (I, personally, am moving back to campus)</li>
</ul> 

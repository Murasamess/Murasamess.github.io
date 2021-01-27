---
layout: post
title: Decoupled Classification 
author: "Lavanya Singh"
presenter: "Lavanya Singh"
date: 2021-01-05
categories: [ML, fairness, society, bias, algorithms]
papers:
- name: "Decoupled Classifiers for Fair and Efficient Machine Learning"
  link: "https://arxiv.org/abs/1707.06613"
- name: "Big Data's Disparate Impact"
  link: "https://www.jstor.org/stable/24758720"
---

## Inspiration

In spring of 2020, I took "Critical Thinking in Data Science," taught by James Waldo and Mike Smith. We 
discussed disparate impact and disparate treatment, two doctrines in employment law. For my final project,
I compared some methods of debiasing classifiers, and the method presented in "Decoupled Classifiers for
Fair and Efficient Machine Learning" was one of them. "Big Data's Disparate Impact" was published in the 
California Law Review, and is different from the kind of thing we usually read. Second II introduces
disparate impact and disparate treatment.

## Discussion

Whenever reading group reads a paper by Cynthia Dwork, we always spend a lot of time on the math. Once 
we wrapped our heads around the math, we discussed the monotonicity condition. The paper requires
that the joint loss function (used to pick the optimal combination of classifiers for each group) is 
monotone decreasing in loss for each group. In other words, if a combination of classifiers achieves
better individual loss for each group, it must also achieve better overall loss. This condition seems 
to be important to make the final search step efficient, but the paper itself says that the search step
is far quicker than the learning step, so we're not sure why this is necessary. 

Section 4.1 argues that a monotone loss function is necessary to prevent lowering accuracy in the name
of fairness. We wondered how this paradigm fits in the context of the paper's goals. After all, we need 
a joint loss function because we're not just picking the best classifier for each group: we want 
something other than the most accurate set of classifiers. The paper is clear that the relationship 
between montonicity and fairness is an open question. 

The paper trains a set of classifiers for each group and then uses the joint loss function to pick 
some combination of these classifiers. We also considered taking both loss and joint loss into account 
while training itself. This might look like replacing the original loss function with the joint loss
function and using a learner that outputs just a single classifier. Alternatively, you could alternate
the update steps between the two loss functions. At worst, this is twice as expensive, and we're not sure
if that's a deal-breaker (we think it's not). What benefit does decoupled classification give you over 
using a joint loss function as you train separate classifiers? The paper does emphasize that this 
method can be applied on top of out-of-the-box learners, whereas our proposal might require a custom
learner.

We also talked about the legal and philosophical implications of this work. After all, decoupled 
classification is illegal in most sensitive contexts, probably because this country has a nasty 
history when it comes to segregation based on protected class attributes. That being said, affirmative
action does explicitly take protected class attributes like race into account. We are not lawyers, but 
are curious about what the legal difference is. 

## Tangents

Speaking of fairness and the law, the California Law Review article said that you're not allowed to 
treat members of protected classes differently. But models that exhibit a disparate impact DO treat 
minorities differently, they just hide it behind an uninterpretable machine learning model. Most of our
models are biased because most of our data is biased because most of our history is biased, so what 
does that mean for disparate treatment? The article did say that disparate treatment has a really 
specific applicability, but it seems like the spirit of the law is violated all the time.

How could you even make room for decoupled classification in the law? Is it affirmative action? Would 
you have to specify which joint loss functions are legal? Maybe I should go to law school...

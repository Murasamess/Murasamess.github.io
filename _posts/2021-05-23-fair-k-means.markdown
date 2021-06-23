---
layout: post
title: "Fair k-Means Clustering"
date: 2020-05-23
author: "Lavanya Singh"
presenter: "Lavanya Singh"
categories: [fairness, ML, society, algorithms]
papers:
- name: "Socially Fair 𝑘-Means Clustering"
  link: "https://arxiv.org/pdf/2006.10085.pdf"
---

## Paper
It's been a while since reading group has read a fairness paper, so this week I 
looked at the papers accepted at ACM FAccT (Fairness, Accountability, and Transparency)
and picked one. We read Ghadiri, Samadi, and Vempala's ["Socially Fair k-Means Clustering"](https://arxiv.org/pdf/2006.10085.pdf),
which presents an algrorithm for, as you might have guessed, fair k-means clustering.

## Discussion
We've read fairness papers before at reading group, but they often focus on "proportionality" as 
a measure of fairness. A clustering is proportionally fair if the proportions of group members, 
where groups usually track social characteristics like gender or race, are the same across 
clusters. During previous reading group sessions, we've discussed tradeoffs between proportionality 
and accuracy. For a hiring classifier, proportionality is really important, but for something like 
k-means clustering, which is often used in resource allocation, accuracy might matter more. This
paper answers that intuition by presenting a definition of fairness based on accuracy. A clustering 
is fair if it imposes a similar accuracy cost (defined as distance from the nearest cluster center) 
across groups. Normal k-means often imposes higher costs on minorities in the dataset.

We spent some time comparing the algorithm presented to the classic Lloyd heuristic for k-means
clustering. The runtime presented for finding the optimal centers during a single iteration 
of Fair-Lloyd is O(k log(l)) where l is the difference in means for different groups. This does 
not include the time it takes to actually calculate the center for each point, so it's not as fast 
as normal Lloyd.

We also wondered about other definitions of fairness. Another way to frame the spirit of fairness
based on accuracy is to notice that minorities in the dataset have ``less of a voice" in 
determining the value of the objective function. Intutively, one way to fix this might be to 
consider a weighted sum of k-means costs as the objective function, where minority groups' k-means 
costs are weighted more heavily. Our hunch is that this approach will be very similar to Ghadiri et.
al's approach (they take the max of the k-means costs across groups). In the case of two groups, 
it's immediate that you can bound this weighted sum (where weights are normalized) in terms of 
the max of the k-means costs across groups. That bound might yield a proof that the two approaches 
converge, but we've been wrong before!



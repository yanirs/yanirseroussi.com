---
title: Transfer learning applies to energy market bidding
author: Yanir Seroussi
type: til
date: 2023-12-14T00:15:00+00:00
url: /til/2023/12/14/transfer-learning-applies-to-energy-market-bidding/
summary: An interesting approach to bidding of energy storage assets, showing that training on New York data is transferable to Queensland.
showBreadcrumbs: true
tags:
  - energy markets
  - machine learning
  - quotes
---

Quoting the abstract of [Transferable Energy Storage Bidder](https://arxiv.org/abs/2301.01233) by Yousuf Baker, Ningkun Zheng, and Bolun Xu:

> Energy storage resources must consider both price uncertainties and their physical operating characteristics when participating in wholesale electricity markets. This is a challenging problem as electricity prices are highly volatile, and energy storage has efficiency losses, power, and energy constraints. This paper presents a novel, versatile, and transferable approach combining model-based optimization with a convolutional long short-term memory network for energy storage to respond to or bid into wholesale electricity markets. We test our proposed approach using historical prices from New York State, showing it achieves state-of-the-art results, achieving between 70% to near 90% profit ratio compared to perfect foresight cases, in both price response and wholesale market bidding setting with various energy storage durations. We also test a transfer learning approach by pre-training the bidding model using New York data and applying it to arbitrage in Queensland, Australia. The result shows transfer learning achieves exceptional arbitrage profitability with as little as three days of local training data, demonstrating its significant advantage over training from scratch in scenarios with very limited data availability.

I'm not sure about the practical implications, but it's interesting that data from New York is informative for Queensland. I also found the approach of predicting the opportunity value function (rather than forecasting prices) to be clever. However, I'm not familiar with research in the field, so this may be standard practice. Still, I will refer back to this paper and its references if I go deeper into energy market bidding.

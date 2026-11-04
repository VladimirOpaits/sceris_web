---
title: "The best explanation on why data analysis protocols should be preregistered, or how I finally fell in love with statistics"
description: "Gelman and Loken's essay on the garden of forking paths: why flexible analysis choices inflate false positives even without p-hacking, why a flat prior hides behind verbal explanations, and why preregistration matters."
tags: [data analysis, statistics, frequentist statistics, bayesian inference]
math: true

paper:
  title: "The garden of forking paths: Why multiple comparisons can be a problem, even when there is no “fishing expedition” or “p-hacking” and the research hypothesis was posited ahead of time"
  authors: "Andrew Gelman and Eric Loken"
  venue: "Unpublished manuscript, Department of Statistics, Columbia University"
  year: 2013
---

[Link to paper](https://sites.stat.columbia.edu/gelman/research/unpublished/p_hacking.pdf)

## My take
Statistics was always confusing for me and other students. It is neither a purely deductive tool like mathematics, built from logical structures and axioms, nor an empirically grounded science like physics, chemistry or bio. I managed to do research, build models and get results without truly understanding some of the key intuitions behind statistical inference. It did not help that there is apparently still a debate between frequentist and Bayesian approaches. I watched countless YouTube videos trying to fill the gap that exercises could not fill. They gave me a basic understanding and showed me which direction to look in, but what finally connected the dots was the more philosophical, epistemic approach to the problem that this essay takes.

Sometimes the problem creeps in not through code or formulas, but at a psychological level. Motivated reasoning makes you draw wrong conclusions from a test by quietly assuming an absurd prior, without ever writing it down. The essay's example is a study of extrasensory perception in students: out of many categories, the authors picked the only one that came out significant (a hit rate of about 53% instead of the 50% expected by chance) and then built a verbal justification for it, one that could just as easily have been built for any other category.

Finding that one category is not even surprising. With $$k$$ independent comparisons at $$\alpha = 0.05$$, the chance that at least one of them comes out "significant" by pure luck is

$$
P(\text{at least one } p < 0.05) = 1 - (1 - 0.05)^k,
$$

which is already about 40% for $$k = 10$$.

The Bayesian view exposes the second mistake. Let $$\theta$$ be the true hit rate and $$\hat\theta \approx 0.53$$ the observed one, with standard error $$\sigma$$. Accepting $$\hat\theta$$ at face value is the same as using a flat prior, $$\theta \sim \mathcal{U}(0, 1)$$, as if a 90% hit rate were just as plausible as 50.5%. But everything we know about the world says that if such an effect exists at all, it is tiny, so a sensible prior is a narrow Gaussian around chance level:

$$
\theta \sim \mathcal{N}(0.5,\ \tau^2), \qquad \tau \ll \sigma.
$$

With a normal approximation to the likelihood, the posterior mean is a weighted average of chance level and the observed rate:

$$
\mathbb{E}[\theta \mid \text{data}] = 0.5 + w\,(\hat\theta - 0.5), \qquad w = \frac{\tau^2}{\tau^2 + \sigma^2}.
$$

If $$\tau$$ is five times smaller than $$\sigma$$, then $$w \approx 0.04$$, and the observed 53% shrinks to about 50.1%, which is practically nothing. The verbal story about why this particular category should work is what quietly smuggles in the flat prior.

I find this especially interesting because it is exactly where statistics and the humanities overlap: the error is not in the arithmetic, but in the story we tell about it.

This reminded me once again that STEM people are often too quick to dismiss philosophy as a way to understand cognitive errors, approaches, and, more generally, how we process information. Plato's allegory of the cave is still what lets me correctly map and process many epistemological questions in scRNA-seq, such as the batch effect problem, where it is not even clear what counts as a batch and what is the important biological signal. I am deeply interested in what philosophy and texts like this can add to my mathematical and scientific ways of thinking.
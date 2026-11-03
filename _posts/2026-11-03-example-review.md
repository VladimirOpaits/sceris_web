---
title: "Example review: how a post is structured"
tldr: "A demo post showing everything the template supports. Delete it once you publish your first real review."
tags: [scrnaseq, ml]
math: true

paper:
  title: "Deep generative modeling for single-cell transcriptomics"
  authors: "Lopez R., Regier J., Cole M. B., Jordan M. I., Yosef N."
  venue: "Nature Methods"
  year: 2018
  doi: "10.1038/s41592-018-0229-2"
  code: "https://github.com/scverse/scvi-tools"
---

## Context

Plain text is written in Markdown. **Bold**, *italic*, `inline code`,
[links](https://example.com).

> Quotes from the paper look like this.

## Formulas

These work when front matter has `math: true`. Inline: $z_n \sim \mathcal{N}(0, I)$,
display:

$$
x_{ng} \mid z_n, \ell_n \sim \mathrm{ZINB}\big(\ell_n \, \rho_g(z_n), \theta_g, \pi_g(z_n)\big)
$$

## Code

```python
import scanpy as sc
import scvi

adata = sc.read_h5ad("pbmc.h5ad")
scvi.model.SCVI.setup_anndata(adata, layer="counts", batch_key="batch")
model = scvi.model.SCVI(adata, n_latent=10)
model.train()
```

## Table

| Method | ARI | NMI |
|-------|-----|-----|
| PCA   | 0.61 | 0.70 |
| scVI  | 0.74 | 0.79 |

## Images

Put files in `assets/img/reviews/<post-name>/` and embed them with a caption
(click opens full size):

{% include figure.html src="/assets/img/reviews/example-review/placeholder.svg" caption="Figure 1 from the paper, *with Markdown* in the caption" %}

{% raw %}
```liquid
{% include figure.html src="/assets/img/reviews/example-review/fig1.png" caption="Figure 1" %}
```
{% endraw %}

Plain Markdown also works: `![alt text](/assets/img/reviews/example-review/fig1.png)`.

## My take

Personal assessment of the paper goes here.

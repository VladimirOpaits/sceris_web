---
title: "Пример обзора: как устроен пост"
tldr: "Демонстрационный пост — показывает все возможности шаблона. Удали его, когда опубликуешь первый настоящий обзор."
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

## Контекст

Обычный текст пишется в Markdown. **Жирный**, *курсив*, `inline code`,
[ссылки](https://example.com).

> Цитаты из статьи удобно оформлять так.

## Формулы

Работают, если в front matter стоит `math: true`. Строчная: $z_n \sim \mathcal{N}(0, I)$,
блочная:

$$
x_{ng} \mid z_n, \ell_n \sim \mathrm{ZINB}\big(\ell_n \, \rho_g(z_n), \theta_g, \pi_g(z_n)\big)
$$

## Код

```python
import scanpy as sc
import scvi

adata = sc.read_h5ad("pbmc.h5ad")
scvi.model.SCVI.setup_anndata(adata, layer="counts", batch_key="batch")
model = scvi.model.SCVI(adata, n_latent=10)
model.train()
```

## Таблица

| Метод | ARI | NMI |
|-------|-----|-----|
| PCA   | 0.61 | 0.70 |
| scVI  | 0.74 | 0.79 |

## Картинки

Положи файл в `assets/img/` и вставь так:

{% raw %}
```markdown
![Подпись]({{ "/assets/img/figure.png" | relative_url }})
```
{% endraw %}

## Моё мнение

Здесь — личная оценка статьи.

# Paper Notes

Мини-обзоры научных статей (ML, bio, data science, биоинформатика, scRNA-seq).
Сайт собирается GitHub Pages из этого репозитория (Jekyll), отдельный CI не нужен.

## Как добавить новый обзор

1. Скопируй шаблон:
   ```bash
   cp _templates/review.md _posts/$(date +%F)-short-name.md
   ```
2. Заполни front matter (`title`, `tldr`, `tags`, блок `paper`) и текст.
3. `git add . && git commit -m "review: short-name" && git push`

Через 1–2 минуты пост появится на сайте.

- Имя файла **обязательно** в формате `ГГГГ-ММ-ДД-slug.md` — иначе Jekyll его не увидит.
- Посты с датой в будущем не публикуются.
- Черновики можно класть в `_drafts/` (без даты в имени) — на сайт они не попадают.
- Формулы: поставь `math: true` в front matter.
- Картинки: в `assets/img/`, вставка `![подпись]({{ "/assets/img/x.png" | relative_url }})`.

## Структура

```
_config.yml          настройки: название, автор, список тем (topics)
_posts/              обзоры
_templates/review.md шаблон нового обзора (не публикуется)
_layouts/            HTML-каркасы: default, page, post
_includes/           куски HTML: шапка, подвал, теги, карточка поста
assets/css/style.css все стили; цвета и шрифты — переменные в :root
index.html           главная (список обзоров)
tags.html            страница тем
about.md             «Обо мне»
```

## Включение GitHub Pages

Settings → Pages → Source: **Deploy from a branch**, Branch: `main`, папка `/ (root)`.

- Репозиторий `<username>.github.io` → сайт на `https://<username>.github.io/`.
- Любое другое имя (например `sceris_web`) → `https://<username>.github.io/sceris_web/`;
  `baseurl` GitHub подставит сам, все ссылки в шаблоне через `relative_url`.

## Локальный просмотр (необязательно)

```bash
gem install --user-install bundler
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve --livereload
# http://localhost:4000
```

## Ограничения GitHub Pages, учтённые в шаблоне

- Только плагины из белого списка (используются `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap`).
- Нельзя генерировать отдельную страницу на каждый тег → все темы на одной странице `/tags/` с якорями.
- Нет серверной логики: поиск/комментарии — только через сторонние JS-сервисы (например, giscus).
- Лимиты: репозиторий/сайт до 1 ГБ, ~100 ГБ трафика в месяц — тяжёлые данные лучше хранить снаружи.

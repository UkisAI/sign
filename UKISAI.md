# UkisAI Sign

This is the source of [sign.ukisai.com](https://sign.ukisai.com), UkisAI's document signing site. It is
[DocuSeal](https://github.com/docusealco/docuseal) 3.3.5 with UkisAI's visual theme. DocuSeal is licensed under
AGPL-3.0 with additional terms (see `LICENSE` and `LICENSE_ADDITIONAL_TERMS`); this modified version is offered under
the same terms, and the DocuSeal attribution is kept in every page that shows it.

## What changed from upstream 3.3.5

- `public/ukisai/`: theme stylesheet, UkisAI logos, mosaic button tiles. Avenir is licensed, so the font files are not
  in this repository; `Dockerfile.ukisai` fetches UkisAI's hosted copy at build time.
- `app/views/layouts/_ukisai_head.html.erb`, plus one line in the `application`, `plain` and `form` layouts that renders it.
- Logos and titles: `shared/_logo`, `shared/_title`, `start_form/_docuseal_logo`, `submit_form/_docuseal_logo`,
  `templates_share_link_qr/_logo`, `layouts/_head_tags`, `shared/_meta`, `pwa/manifest.json`.
- `shared/_powered_by`: keeps "Powered by DocuSeal" and adds a link to this source code.
- `pages/landing`: a short UkisAI home page in place of the DocuSeal product page.
- Favicons and `public/preview.png`.

No Ruby, JavaScript or database code is changed.

## Build

`Dockerfile.ukisai` layers these files onto the official `docuseal/docuseal:3.3.5` image:

```sh
docker build -f Dockerfile.ukisai -t ukisai-sign .
```

# hussainhadah.com

Source for Hussain Hadah's Quarto website.

## Local development

The production workflow uses Quarto 1.8.26. Install that version, then run:

```sh
quarto preview
```

The preview opens at <http://localhost:5555>. Build the production files in `docs/` with:

```sh
quarto render
```

## Interface structure

- `html/hh.scss` contains the shared color, type, spacing, navigation, card, gallery, and responsive rules.
- `html/research/listing.ejs` renders research cards. `html/research/filter.html` supplies the cross-section topic filter.
- The homepage, research archive, personal gallery, teaching page, and CV page use named component classes in their `.qmd` files rather than page-specific inline styles.

Check layout changes at both 390px and 1440px widths. The mobile research filters intentionally scroll horizontally.

## Research status updates

Paper status appears in each research page's `pub-info.venue` and citation, homepage highlights in `index.qmd`, and `cv/publications.bib`. Conditionally accepted papers appear under Publications in the CV, with their status stated in the entry's note.

After changing the bibliography, rebuild both CV PDFs before rendering the website:

```sh
(cd cv && latexmk -pdf -interaction=nonstopmode -halt-on-error cv.tex hadah-cv.tex)
quarto render
```

## Statement updates

Replace `cv/Hadah_Research.pdf`, `cv/Hadah_Teaching.pdf`, and `cv/Hadah_Diversity.pdf` with the current statements, keeping those filenames. `_quarto.yml` explicitly includes them as publishing resources.

Run `quarto render` to refresh the copies in `docs/cv/`. The homepage links to all three PDFs, and the teaching page links to the teaching statement. Commit and push the updated PDFs and rendered files to deploy them. Changing files locally does not update the live site.

## Publishing

Pushing to `main` or `master` runs `.github/workflows/netlify-publish.yml`. The workflow installs Quarto 1.8.26, renders the project, and publishes the result to the Netlify site in `_publish.yml`. The repository must provide a `NETLIFY_AUTH_TOKEN` Actions secret. The workflow can also be run manually from GitHub Actions.

## Credits

The original design drew from [Marvin Schmitt's Quarto tutorial](https://www.marvinschmitt.com/blog/website-tutorial-quarto/), [Drew Dimmery's academic website guide](https://ddimmery.com/posts/quarto-website), and [Andrew Heiss's Quarto template](https://github.com/andrewheiss/ath-quarto).

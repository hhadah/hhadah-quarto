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

## Publishing

Pushing to `main` or `master` runs `.github/workflows/netlify-publish.yml`. The workflow installs Quarto 1.8.26, renders the project, and publishes the result to the Netlify site in `_publish.yml`. The repository must provide a `NETLIFY_AUTH_TOKEN` Actions secret. The workflow can also be run manually from GitHub Actions.

## Credits

The original design drew from [Marvin Schmitt's Quarto tutorial](https://www.marvinschmitt.com/blog/website-tutorial-quarto/), [Drew Dimmery's academic website guide](https://ddimmery.com/posts/quarto-website), and [Andrew Heiss's Quarto template](https://github.com/andrewheiss/ath-quarto).

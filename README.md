# nataliestors.de

Source of https://nataliestors.de, built with Jekyll and the Minimal Mistakes theme. GitHub Actions builds the site on every push to `master` and deploys it to GitHub Pages.

## Local preview

```bash
mise install                                  # Ruby 3.4 and Node 22
bundle install                                # Jekyll, the theme, and the plugins
npm ci --ignore-scripts && ./_copy_assets.sh  # Font Awesome, Academicons, _includes/head.html
bundle exec jekyll serve                      # http://localhost:4000/
```

Without the npm step, the preview shows no icons. `_copy_assets.sh` copies the icon fonts from `node_modules/` into `assets/` and generates `_includes/head.html` from the head of the installed theme, so run it again after `bundle install` or `npm ci` installs a new version. Git tracks none of the files that the script writes.

## Updates

`Gemfile.lock` and `package-lock.json` are committed. Dependabot opens a pull request for each new release of a gem, an npm package, or a GitHub Action, and the pull request build shows whether the site still builds. Check the local preview before merging a new major version of the theme or of Font Awesome.

[![CircleCI](https://circleci.com/gh/18F/cv_faq.svg?style=svg)](https://circleci.com/gh/18F/cv_faq)

# faq.coronavirus.gov

A Coronavirus FAQ for the United States of America.

## API

A JSON API is available for site content. See the [API documentation](https://faq.coronavirus.gov/api/).

## Technology overview

This website is developed using the [U.S. Web Design System](https://designsystem.digital.gov), is deployed on [Federalist](https://federalist.18f.gov/), search is provided by [Search.gov](https://search.gov/), and analytics are provided by the [Digital Analytics Program](https://digital.gov/guides/dap/). This code uses the [Jekyll](https://jekyllrb.com) site engine.

You may want to familiarize yourself with:

- [Jekyll](https://jekyllrb.com/docs/) - The primary site engine that builds your code and content.
- [Front Matter](https://jekyllrb.com/docs/frontmatter) - The top of each page/post includes keywords within `--` tags. This is meta data that helps Jekyll build the site, but you can also use it to pass custom variables.
- [U.S. Web Design System](https://designsystem.digital.gov).

## Getting acquainted

The [\_categories](_categories) folder contains the question groups, or categories, which are displayed on the site. Its `title` property is what is visible on the site.

In the [\_content](_content) folder you’ll find a folder which matches the `name` property of a category for each category. Inside that folder is a file representing each question in that category, which has a `category` property which also matches the category’s `name` property.

For more detailed coverage, see the [Content management guide](https://github.com/18F/cv_faq/wiki/Content-management-in-cv_faq).

### How to edit
Content on this site is generated by federal government agencies who submit FAQ content to our team for publishing. To ensure we’re all using consistent voice and style, we have a [content strategy guidance](https://github.com/18F/cv_faq/wiki/Content-strategy-guidance).

### Adding an urgent alert
On the `index.html` you can add an urgent USWDS-style banner by changing the front matter. Turn the `banner.display` key to `true` to display the banner.

#### Icons
Adding an top questions icon - if you need to add an additional icon add it to the `_assets/images/icons` directory.

And then if you'd like to use in a top question - add it in the `_data/homepage_promotion.yml`.

### Editing by downloading and running the source code

The easiest way to get started locally, after the repository is forked, is to use [Docker](https://www.docker.com/). After Docker is installed and running, run:

```bash
docker-compose build
docker-compose up
```

This will build and install all required dependencies, then compile the site, and finally start a development server which is accessible at [localhost:4000](http://localhost:4000/). The server will recompile the site automatically as files change. Use <kbd>CTRL</kbd> + <kbd>C</kbd> to shutdown the server.

Do not edit files in the `_site/` folder. These files are auto-generated, and any change you make in the folder will be overwritten.

#### Running without Docker

To run without Docker, you’ll need the version of Ruby that’s specified in [.ruby-version](.ruby-version). Then, to install dependencies:

```bash
gem install bundler
bundle install
npm install
```

Finally, to start the site, run:

```bash
npm start
```

Open your web browser to [localhost:4000](http://localhost:4000/) to view your site. The server will recompile the site automatically as files change. Use <kbd>CTRL</kbd> + <kbd>C</kbd> to shutdown the server.

## Automated testing

Tests are automatically run on commits and pull requests by [CircleCI](https://circleci.com/gh/18F/cv_faq). They can be run manually:

```bash
npm test
```

The test suite includes:

- [HTMLProofer](https://github.com/gjtorikian/html-proofer), which looks for [some basic accessibility issues, for broken links, and more](https://github.com/gjtorikian/html-proofer#whats-tested). We’ve also extended it [to check for well-formed links](htmlproofer/target_blank_checks.rb).
- [jest](https://jestjs.io/), [jest-puppeteer](https://github.com/smooth-code/jest-puppeteer), and [puppeteer](https://github.com/puppeteer/puppeteer) for custom integration tests. See what’s tested in the [test directory](test).

## Initial localization support
The jekyll template has a feature to support localization.

Languages supported will be added to the `i18n` portion of the site config in `_config.yml`.

To add in localization back into the hero component, uncomment the comment in the `_includes/hero.html` around the `i18n-controls` paragraph tag.

The plugin for parsing a the  language of a file can be found in `_plugins/jekyll_parse_language.rb`

### Adding localized content
- Append `.lang-{2 character language code}` to `_content` files to indicate their language.
- This creates a `/{2 character language code}/` output directory in the site folder.
- We can use `{{ post.lang }}` in files to reference the current language and link to the right language in URLs.
- The default language is `en` for files without the suffix.

This approach keeps each translation next to each other in directories, and allows us to filter based on `page.lang` on pages.

## Maintaining a secure codebase

See [SECURITY](SECURITY.md).

## Contributing and how to open, merge, and deploy pull requests

See [CONTRIBUTING](CONTRIBUTING.md).

## Public domain

This project is in the worldwide [public domain](LICENSE.md). As stated in [CONTRIBUTING](CONTRIBUTING.md):

> This project is in the public domain within the United States, and copyright
> and related rights in the work worldwide are waived through the [CC0 1.0
> Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).
>
> All contributions to this project will be released under the CC0 dedication.
> By submitting a pull request, you are agreeing to comply with this waiver of
> copyright interest.

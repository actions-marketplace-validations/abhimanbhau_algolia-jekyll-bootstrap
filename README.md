# aloglia-jekyll-bootstrap
Action to bootstrap Algolia search and updates search index for GitHub pages

### References:

* Official Algolia docs [jekyll-algolia documentation](https://community.algolia.com/jekyll-algolia/getting-started.html).
* [GitHub composite actions guide](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action)
* [Building and testing Ruby](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-ruby)
* [@setup-ruby official guide](https://github.com/ruby/setup-ruby#caching-bundle-install-automatically)

To use it to bootstrap your GitHub pages Jekyll blog or website use following boiler plate code to create a action for your repo

```yaml
on:
  push:
    branches:
      - master

name: algolia-search
jobs:
  algolia-search:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: ruby/setup-ruby@v1
        with:
          ruby-version: '3.1'
          bundler-cache: true
      - name: Algolia Jekyll Bootstrap
        uses: abhimanbhau/algolia-jekyll-bootstrap@v1
        with:
          API_KEY: '${{ secrets.ALGOLIA_API_KEY }}'
```

***
NOTE: Make sure your create a secret for the action under repo settings with key 'ALGOLIA_API_KEY' and value to your Algolia Admin Key

___This repo is not affiliated with Algolia.___
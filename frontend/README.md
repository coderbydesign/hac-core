[![Build Status](https://travis-ci.com/RedHatInsights/hac-core-frontend.svg?branch=master)](https://travis-ci.com/RedHatInsights/hac-core-frontend)

# hac-core-frontend

React.js starter app for Red Hat Insights products that includes Patternfly 4 and shared Red Hat cloud service frontend components.

## Getting started

You can choose from either webpack proxy (simple to use) or more config heavy legacy insights-proxy

### Run with webpack proxy

1. ```yarn install```

2. ```yarn start:proxy``` / ```yarn start:beta:proxy```

Update `config/dev.webpack.config.js` according to your application URL. [Read more](https://github.com/RedHatInsights/frontend-components/tree/master/packages/config#useproxy).

### Run with insights proxy

[Insights Proxy](https://github.com/RedHatInsights/insights-proxy) is optional to run the hac-core frontend application.
```
SPANDX_CONFIG="$(pwd)/hac-core-frontend/profiles/local-frontend.js" bash insights-proxy/scripts/run.sh
```

Open new terminal and run the app

1. ```yarn install```

2. ```yarn start```
    - starts webpack bundler and serves the files with webpack dev server


### Testing

`yarn verify` will run `yarn lint` (eslint) and `npm test` (Jest)

## Deploying

- The starter repo uses Travis to deploy the webpack build to another Github repo defined in `.travis.yml`
  - That Github repo has the following branches:
    - `ci-beta` (deployed by pushing to `master` or `main` on this repo)
    - `ci-stable` (deployed by pushing to `ci-stable` on this repo)
    - `qa-beta` (deployed by pushing to `qa-beta` on this repo)
    - `qa-stable` (deployed by pushing to `qa-stable` on this repo)
    - `prod-beta` (deployed by pushing to `prod-beta` on this repo)
    - `prod-stable` (deployed by pushing to `prod-stable` on this repo)
- Travis uploads results to RedHatInsight's [codecov](https://codecov.io) account. To change the account, modify CODECOV_TOKEN on https://travis-ci.com/.

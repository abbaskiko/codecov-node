# Codecov NodeJS Uploader

[![NPM version][npm-image]][npm-url]
[![Build Status][github-actions-image]][github-actions-url]
[![Build Status][travis-image]][travis-url]
[![codecov.io](https://codecov.io/github/codecov/codecov-node/coverage.svg?branch=master)](https://codecov.io/github/codecov/codecov-node?branch=master)
[![Dependency Status][depstat-image]][depstat-url]
[![Dev Dependency Status][devdepstat-image]][devdepstat-url]

[Codecov.io](https://codecov.io/) support for node.js.

## Installation:

Add the latest version of `codecov` to your package.json:

```
npm install codecov --save-dev
```

or

```
yarn add codecov --dev
```

## Usage:

This script ( `bin/codecov` ) detect your CI provider and all coverage reports and uploads them to Codecov.

Once your app is instrumented for coverage, and building, simply call `./node_modules/.bin/codecov`.

This library currently supports the following CI companies: [Travis CI](https://travis-ci.org/), [Travis](https://travis-ci.com/), [Appveyor](https://appveyor.com/), [CircleCI](https://circleci.com/), [Cirrus CI](https://cirrus-ci.org/), [Codeship](https://codeship.io/), [Drone](https://drone.io/), [Jenkins](http://jenkins-ci.org/), [Shippable](https://shippable.com/), [Semaphore](https://semaphoreapp.com/), [Wercker](https://wercker.com/), [Snap CI](https://snap-ci.com/), [Buildkite](https://buildkite.com/), [AWS CodeBuild](https://aws.amazon.com/codebuild/).

#### Upload repo tokens

> Repo tokens are **not** required for public repos tested on Travis-Org, CircleCI or AppVeyor.

Repo tokens are necessary to distinguish your repository from others. You can find your repo token on your repository page at Codecov. Set this unique uuid to `CODECOV_TOKEN` in your environment variables.

```
export CODECOV_TOKEN=":uuid-repo-token"
# or
./node_modules/.bin/codecov --token=:token
# or
./node_modules/.bin/nyc report --reporter=text-lcov | ./node_modules/.bin/codecov --pipe
```

#### [Istanbul](https://github.com/gotwarlost/istanbul)

**With Mocha:**

```sh
istanbul cover ./node_modules/mocha/bin/_mocha -- -R spec
./node_modules/.bin/codecov
```

**With Jasmine:**

```sh
istanbul cover jasmine-node --captureExceptions spec/
./node_modules/.bin/codecov
```

**With Tape:**

```sh
istanbul cover test.js
./node_modules/.bin/codecov
```

[appveyor-url]: https://ci.appveyor.com/project/eddiemoore/codecov-node-s38o6/branch/master
[github-actions-image]: https://github.com/codecov/codecov-node/workflows/Node%20CI/badge.svg
[github-actions-url]: https://github.com/codecov/codecov-node/actions?query=workflow%3A%22Node+CI%22
[travis-image]: https://travis-ci.org/codecov/codecov-node.svg?branch=master
[travis-url]: https://travis-ci.org/codecov/codecov-node
[npm-url]: https://npmjs.org/package/codecov
[npm-image]: https://img.shields.io/npm/v/codecov.svg
[depstat-url]: https://david-dm.org/codecov/codecov-node
[depstat-image]: https://david-dm.org/codecov/codecov-node/status.svg
[devdepstat-url]: https://david-dm.org/codecov/codecov-node?type=dev
[devdepstat-image]: https://david-dm.org/codecov/codecov-node/dev-status.svg

**With NYC**

```
nyc npm test
nyc report --reporter=text-lcov > coverage.lcov
./node_modules/.bin/codecov
```

## Troubleshooting

If you're seeing an **HTTP 400 error when uploading reports to S3**, make sure you've updated to at least version 3.7.0.

## Change Log

- v2.0.0 No longer supports node v0.10 because of the execSync.
- v2.0.1 Publish as latest instead of next.
- v2.0.2 Display correct version number in console.
- v2.1.0 Flags supported http://docs.codecov.io/docs/flags
- v2.2.0 Support for Jenkins Blue Ocean. Clean reports after upload. Fix for Gitlab.
- v2.3.0 Added support for Windows. Updated dependencies.
- v3.0.0 No longer supports node v0.12 because of new version of request
- v3.0.1 Security fixes
- v3.0.2 Security fixes
- v3.0.3 Support non-git/hg root dirs
- v3.0.4 Security fixes
- v3.1.0 Custom yaml file. Allow codecov token from yml file.
- v3.2.0 Added azure pipelines
- v3.3.0 Added pipe with `--pipe`, `-l`
- v3.4.0 Added Heroku CI support
- v3.5.0 Added TeamCity support
- v3.6.0 Added AWS CodeBuild and Semaphore2
- v3.6.1 Fix for Semaphore
- v3.6.2 Command line args sanitized fix
- v3.6.3 Fix for AWS Codebuild & package updates
- v3.6.4 Fix Cirrus CI
- v3.7.0 Remove the X-Amz-Acl: public-read header
- v3.7.1 Move to execFileSync and security fixes
- v3.7.2 Fix issue with network and file finding
  .

# Protractor in a docker container

This image allows to run javascript tests in a headless machine like a CI server.

This image support protractor test under chrome.

Unfortunately, chrome doesn't support container (https://github.com/travis-ci/travis-ci/issues/938), you need to start chrome with --no-sandbox argument to avoid this.

To configure protractor, use this snippets:

### protractor:

    capabilities: {
      'browserName': 'chrome',
      'chromeOptions': {
        'args': ['no-sandbox']
      }
    },

## Gitlab CI

To run protractor on gitlab ci, just use this image, and configure protractor as above.

Here is example of ".gitlab-ci.yml" file:

```
image: milosh012/docker-protractor-chrome:latest

cache:
  paths:
  - node_modules/

test_async:
  script:
   - npm install
   - node ./node_modules/protractor/bin/webdriver-manager update
   - npm test
```

## On Docker Hub

https://hub.docker.com/r/milosh012/docker-protractor-chrome/

```docker pull milosh012/docker-protractor-chrome```

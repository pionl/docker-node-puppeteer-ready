# Docker image based on official node image with with GoogleChrome/puppeteer support

## Pre-installed packages:

- Chrome requirements for running [puppeteer](https://github.com/GoogleChrome/puppeteer)
- git and openssh-server for cloning support. Extends [docker-node-clone-ready](https://github.com/pionl/docker-node-clone-ready)

## Usage

> This image should not be used running production services. It is designed mainly for a CI.

```
docker run --IMAGE_NAME--:17 google-chrome-stable --version
```

### Gitlab CI usage

Gitlab CI usage

```shell
test:review:
  image: --IMAGE_NAME--:17
  stage: acceptance
  variables:
    PUPPETEER_SKIP_CHROMIUM_DOWNLOAD: "true"
    PUPPETEER_EXECUTABLE_PATH: "/usr/bin/google-chrome-stable"
  tags:
    - docker
  script:
    - npm install
    - ./node_modules/.bin/codeceptjs run
  only:
    refs:
      - merge_requests

```

### Puppeteer

Use already installed chromium by providing a path:

```
export PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true
...
browser.launch({executablePath: 'google-chrome-stable'})
```

### Tags

![https://github.com/--IMAGE_NAME--](https://img.shields.io/github/license/--IMAGE_NAME--?style=flat-square)
--TAGS--

## Built With

> This package is powered by docker work flow cli tool [wf-docker](https://github.com/wrk-flow/wf-docker).

* NodeJS (multiple versions)

## Find Us

* [GitHub](https://github.com/--IMAGE_NAME--)
* [Docker Hub](https://cloud.docker.com/repository/docker/--IMAGE_NAME--)

## Contributions

1. Run `npm install -g wf-docker`
2. Change the `Dockerfile.template`
3. For new php versions edit `wfdocker.json` and `tags` property
4. Use `wf-docker build` to build image, `wf-docker push`, `wf-docker build-push`

> See [wf-docker](https://github.com/wrk-flow/wf-docker) how to use

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

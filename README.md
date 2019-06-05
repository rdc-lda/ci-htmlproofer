# CI build Docker: htmlproofer

CI Docker image for performing HTML proofing

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

In order to develop / test, you need the following tools installed:

* [Docker](https://docs.docker.com/docker-for-mac/install/) 
* [GNU Make](http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/) 3.8 or higher

### And coding style tests

All documents should respect the Markdown language (install a linter in your studio), the following [Vuepress Markdown extensions](https://vuepress.vuejs.org/guide/markdown.html) and [Vuepress enhanced Examples](http://vuepress-enhanced-examples.surge.sh/#overview) can be used.

## Built With

* Docker

### Build Docker with Tini bundled

~~~bash
# Build the Docker locally
#  -- see output how to run this Docker on your machine
$ make image

# Push Docker to the Docker Registry
$ make push
~~~

## Deployment

Use the Docker image in your CI tooling, an examples for have been provided below.

### CircleCI

Just copy the HTML under the `dist/` directory to your webserver and you should be good to go.

~~~yaml

~~~

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/rdc-lda/fintech-blogs/tags).

## Authors

* **Robin Huiser** - *Initial work* - [robinhuiser](https://github.com/robinhuiser)

See also the list of [contributors](CONTRIBUTORS.md) who participated in this project.

## License

This project is licensed under the Apache License - see the [LICENSE](LICENSE) file for details

## Acknowledgments

* Thanks to Bart Reunes for the initial Docker configuration

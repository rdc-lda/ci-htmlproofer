# CI build Docker: HTML Proofer

CI Docker image for performing HTML proofing based upon Ruby Gem [html-proofer](https://github.com/gjtorikian/html-proofer).

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

In order to develop / test, you need the following tools installed:

* [Docker](https://docs.docker.com/docker-for-mac/install/)
* [GNU Make](http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/) 3.8 or higher

## Built With

* Docker

### Build Docker

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

Just copy the YAML into your build definition:

~~~yaml
  # Validate the generated HTML
  validate:
    docker:
      - image: rdclda/ci-htmlproofer:latest
    working_directory: ~/my-html
    environment:
      VUEPRESS_BUILD_DIR: dist
    steps:
      - attach_workspace:
          # Must be absolute path or relative path from working_directory
          at: ~/my-html

      # Test the generated HTML
      - run:
          name: Test our generated HTML files
          command: |
            htmlproofer $VUEPRESS_BUILD_DIR --allow-hash-href --check-html \
            --empty-alt-ignore --disable-external
~~~

...and enable to validate step after the build phase in the overall flow:

~~~yaml
# Glue the jobs together
workflows:
  version: 2
  build_and_publish:
    jobs:
      - build
      - validate:
          requires:
            - build
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

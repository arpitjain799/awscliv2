# AWS CLI v2

Wrapper for dockerized [AWS CLI v2](https://github.com/aws/aws-cli/tree/v2).
Uses [amazon/aws-cli](https://hub.docker.com/r/amazon/aws-cli) Docker image.

- [AWS CLI v2](#aws-cli-v2)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Versioning](#versioning)
  - [Latest changes](#latest-changes)

## Installation

Install [Docker](https://docs.docker.com/get-docker/).

```bash
pip install awscliv2
```

## Usage

Container uses two volumes:

- `$HOME/.aws` -> `/root/.aws`
- `$(cwd)` -> `/aws`

```bash
# alias for
# docker run --rm -it -v ~/.aws:/root/.aws -v $(pwd):/aws amazon/aws-cli $@
awsv2 s3 ls

# or as a python module
python -m awscliv2 s3 ls
```

Add new profile from ENV variables:

```bash
AWS_ACCESS_KEY_ID='my-access-key'
AWS_SECRET_ACCESS_KEY='my-secret-key'

# --configure profile_name access_key secret_key region_name
awsv2 --configure profile_name ${AWS_ACCESS_KEY_ID} ${AWS_SECRET_ACCESS_KEY} us-west-1
```

## Versioning

`awscliv2` version follows [PEP 440](https://www.python.org/dev/peps/pep-0440/).

## Latest changes

Full changelog can be found in [Changelog](./CHANGELOG.md).
Release notes can be found in [Releases](https://github.com/vemel/awscliv2/releases).
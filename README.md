# stale-md

[![CircleCI](https://dl.circleci.com/status-badge/img/gh/mkotsollaris/stale-md/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/mkotsollaris/stale-md/tree/main)

Find stale documentation through CI.

`stale-md` is a CircleCI orb that identifies stale documentation (ie 90 days of unchanged `.md` file) and warns developers on maintaining their documentation.

# Usage

```yml
version: 2.1

orbs:
  stale-md: mkotsollaris/stale-md@0.0.3
  orb-tools: circleci/orb-tools@11.1

jobs:
  scan:
    docker:
      - image: cimg/base:current
    steps:
      - checkout
      - stale-md/scan

workflows:
  main:
    jobs:
      - scan
```

# Options

```yml
parameters:
  IGNORED_FILES:
    type: string
    default: "./.github/PULL_REQUEST_TEMPLATE/PULL_REQUEST.md"
    description: "files to be ignored (space-separated)"
  DAYS_THRESHOLD:
    type: string
    default: "90"
    description: "Time threshold in days"
```

[Example here](./src/commands/scan.yml).

# Motivation

Inspired by [Software Engineering at Google](https://www.goodreads.com/book/show/48816586-software-engineering-at-google), where there was a reference that Google runs a similar pattern internally to embrace continuous software engineering developments and constantly update their documentation.

By utilizing this orb command, developers are reminded that while their software updates so does their documentation. This orb aims to treat documentation as a first-class citizen, similar to production level code where documentation is always remaining up to date.

# Resources

- [Documentation - "Software Engineering at Google" Chapter Review](https://menelaos.dev/documentation-google-swe-book/)

# License

[MIT](./LICENSE)

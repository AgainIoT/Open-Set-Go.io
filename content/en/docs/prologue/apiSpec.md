---
title: "API Spec"
description: "Show our Open-Set-Go Server's API specifications"
lead: "Show our Open-Set-Go Server's API specifications."
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "prologue"
weight: 130
toc: true
---

| Method | Request Path                         | Request Body                                    | Response Body                        | Description                                 |
| ------ | ------------------------------------ | ----------------------------------------------- | ------------------------------------ | ------------------------------------------- |
| POST   | /auth/github-login?code=\<authCode\> |                                                 |                                      | GitHub OAuth Login                          |
| POST   | /auth/github-logout                  | only need cookies                               |                                      | Remove Cookies                              |
| GET    | /user/profile                        | only need cookies                               | [Response Body](#userprofile)        | User Info for user profile                  |
| GET    | /user/grantedInfo                    | only need cookies                               | [Response Body](#usergrantedinfo)    | userInfo with org                           |
| POST   | /repo                                | cookies + [Request Body](#repocheckduplication) | Status will send(NOT FOUND or OK)    | userInfo with org                           |
| GET    | /repo/checkDuplication               | cookies + [Request Body](#repo)                 | true/false(Boolean)                  | check repository is duplicate               |
| POST   | /mail                                | only need cookies                               | Status will send(NOT FOUND or OK)    | send mail to user(after respository create) |
| POST   | /file                                | cookies + [Request Body](#file)                 | Status will send(NOT FOUND or OK)    | upload file to repository                   |
| GET    | /file/supportedEnv                   |                                                 | [Response Body](#filesupportedenv)   | give supportedEnv                           |
| GET    | /file/license                        |                                                 | [Response Body](#filelicense)        | get license information                     |
| GET    | /file/pr                             |                                                 | [Response Body](#filepr)             | get prs information                         |
| GET    | /file/pr/\<id>                       |                                                 | [Response Body](#fileprid)           | get pr information only id                  |
| GET    | /file/contributing                   |                                                 | [Response Body](#filecontributing)   | get contributings information               |
| GET    | /file/contributing/\<id>             |                                                 | [Response Body](#filecontributingid) | get contributings information only id       |
| GET    | /file/readme                         |                                                 | [Response Body](#filereadme)         | get readmes information                     |
| GET    | /file/readme/\<id>                   |                                                 | [Response Body](#filereadmeid)       | get readmes information only id             |

### /user/profile

#### Response Body

```json
{
  "id": "ymw0407",
  "name": "Yun Min Woo",
  "avatar": "https://avatars.githubusercontent.com/u/77202633?v=4"
}
```

### /user/grantedInfo

#### Response Body

```json
{
  "id": "ymw0407",
  "avatar": "https://avatars.githubusercontent.com/u/77202633?v=4",
  "org": [
    {
      "id": "webOS-KOSS",
      "avatar": "https://avatars.githubusercontent.com/u/108121726?v=4"
    },
    {
      "id": "AgainIoT",
      "avatar": "https://avatars.githubusercontent.com/u/128156954?v=4"
    },
    {
      "id": "C-Snake",
      "avatar": "https://avatars.githubusercontent.com/u/133626056?v=4"
    }
  ]
}
```

### /repo

#### Request Body

```json
{
  "owner": "AgainIoT",
  "repoName": "test2",
  "description": "test22"
}
```

### /repo/checkDuplication

#### Request Body

```json
{
  "userName": "AgainIoT",
  "repoName": "Open-Set-Go"
}
```

### /file

#### Request Body

```json
{
  "userName": "AgainIoT",
  "repoName": "Open-Set-Go",
  "language": "JavaScript(Node.js)",
  "framework": "Express.js",
  "gitignore": ["VisualStudioCode", "Linux"],
  "PRTemplate": "### markdown",
  "IssueTemplate": [], // empty array required now
  "contributingMd": "### contributing.md",
  "readmeMd": "### readme.md",
  "license": "https://www.gnu.org/licenses/gpl-3.0.txt"
}
```

### /file/supportedEnv

#### Request Body

```json
[
  {
    "language": "JavaScript(Node.js)",
    "frameworks": [
      {
        "framework": "React",
        "path": "/React"
      },
      {
        "framework": "Express.js",
        "path": "/Expressjs"
      }
    ]
  },
  {
    "language": "TypeScript(Node.js)",
    "frameworks": [
      {
        "framework": "NestJS",
        "path": "/NestJS"
      }
    ]
  }
]
```

### /file/license

#### Response Body

```json
[
  {
    "priority": 0,
    "license": "Apache License 2.0",
    "description": "A permissive license whose main conditions require preservation of copyright and license notices. Contributors provide an express grant of patent rights. Licensed works, modifications, and larger works may be distributed under different terms and without source code.\n",
    "conditions": {
      "permissions": [
        "Commercial use",
        "Modification",
        "Distribution",
        "Patent use",
        "Private use"
      ],
      "limitations": ["Trademark use", "Liability", "Warranty"],
      "conditions": ["License and copyright notice", "State changes"]
    },
    "url": "https://www.apache.org/licenses/LICENSE-2.0.txt"
  },
  {
    "priority": 1,
    "license": "GNU GENERAL PUBLIC LICENSE v3.0",
    "description": "Permissions of this strong copyleft license are conditioned on making available complete source code of licensed works and modifications, which include larger works using a licensed work, under the same license. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights.\n",
    "conditions": {
      "permissions": [
        "Commercial use",
        "Modification",
        "Distribution",
        "Patent use",
        "Private use"
      ],
      "limitations": ["Liability", "Warranty"],
      "conditions": [
        "License and copyright notice",
        "State changes",
        "Disclose source",
        "Same license"
      ]
    },
    "url": "https://www.gnu.org/licenses/gpl-3.0.txt"
  },
  {
    "priority": 2,
    "license": "MIT License",
    "description": "A short and simple permissive license with conditions only requiring preservation of copyright and license notices. Licensed works, modifications, and larger works may be distributed under different terms and without source code.\n",
    "conditions": {
      "permissions": [
        "Commercial use",
        "Modification",
        "Distribution",
        "Patent use",
        "Private use"
      ],
      "limitations": ["Liability", "Warranty"],
      "conditions": ["License and copyright notice"]
    },
    "url": "https://www.mit.edu/~amini/LICENSE.md"
  }
]
```

### /file/pr

#### Response Body

```json
[
  {
    "_id": "64f175c218eed0c9b21a2f2e",
    "title": "preset1",
    "repoName": "AgainIoT/Open-Set-Go",
    "repoUrl": "https://github.com/AgainIoT/Open-Set-Go",
    "content": "### Describe changes\n\n_Describe a summary of the changes and the related issue to communicate to the maintainers why we should accept this pull request._\n\n### Issue number or link\n\n### Types of changes\n\nWhat is the type of code change?\n_Put an `x` in the boxes that apply_\n\n- [ ] Bugfix (changes that resolve errors)\n- [ ] New feature (changes which adds functionality)\n- [ ] Breaking change (big changes that affect existing functionality)\n- [ ] Documentation Update\n\n### Checklist\n\n_Put an `x` in the boxes that apply. You can also fill these out after creating the PR. If you're unsure about any of them, don't hesitate to ask. We're here to help! This is simply a reminder of what we are going to look for before merging your code._\n\n- [ ] I have read the \"README.md\"\n- [ ] My code follows the style guidelines of this project\n- [ ] My changes generate no new warnings\n- [ ] Lint and unit tests pass locally with my changes\n- [ ] I have added tests that prove my fix is effective or that my feature works\n- [ ] I have added necessary documentation\n- [ ] Any dependent changes have been merged and published in downstream modules\n\n### Further comments\n\n_Please let me know if there's anything else to explain_"
  },
  {
    "_id": "64f2fedb2a1079c11a9a646e",
    "title": "simple-preset",
    "repoName": "michaelkolesidis/javascript-software-synthesizer",
    "repoUrl": "https://github.com/michaelkolesidis/javascript-software-synthesizer",
    "content": "### Describe your changes\n\n### Issue ticket number and link\n\n### Checklist before requesting a review\n\n- [ ] I have performed a self-review of my code\n- [ ] If it is a core feature, I have added thorough tests.\n- [ ] Do we need to implement analytics?\n- [ ] Will this be part of a product update? If yes, please write one phrase about this update.\n\nThanks for contributing to JSS-01 | JavaScript Software Synthesizer!"
  },
  {
    "_id": "64f324482a1079c11a9a6470",
    "title": "detail-preset",
    "repoName": "OpenRoberta/openroberta-lab",
    "repoUrl": "https://github.com/OpenRoberta/openroberta-lab",
    "content": "## Description\n\nPlease include a summary of the change and which issue is fixed. Please also include relevant motivation and context. List any dependencies that are required\nfor this change.\n\nPlease *never* include a issue number (as #NUMBER) taken from our github issue tracker in the pull request. If the pull request is changed again and again, this\nfloods the issue with irrelevant commit numbers. Of course the *pure* NUMBER can be used for documentation purposes. If the pull request is accepted, the issue\nnumber will be added during that step.\n\n### Type of change\n\nPlease delete options that are not relevant.\n\n- [ ] Bug fix (non-breaking change which fixes an issue)\n- [ ] New feature (non-breaking change which adds functionality)\n- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)\n- [ ] This change requires a documentation update\n\n## How Has This Been Tested?\n\nPlease describe the tests that you ran to verify your changes. Provide instructions so we can reproduce. Please also list any relevant details for your test\nconfiguration\n\n**Test Configuration**:\n\n* Firmware version:\n* Hardware:\n* Toolchain:\n* SDK:\n* OS:\n\n## Checklist:\n\n- [ ] My code follows the style guidelines of this project\n- [ ] I have performed a self-review of my own code\n- [ ] I have commented my code, particularly in hard-to-understand areas\n- [ ] I have made corresponding changes to the documentation\n- [ ] My changes generate no new warnings\n- [ ] I have added tests that prove my fix is effective or that my feature works\n- [ ] New and existing unit tests pass locally with my changes\n- [ ] Any dependent changes have been merged and published in downstream modules"
  },
  {
    "_id": "64f326072a1079c11a9a6471",
    "title": "comment-preset",
    "repoName": "inversify/InversifyJS",
    "repoUrl": "https://github.com/inversify/InversifyJS",
    "content": "<!--- Provide a general summary of your changes in the Title above -->\n\n### Description\n\n<!--- Describe your changes in detail -->\n\n### Related Issue\n\n<!--- This project only accepts pull requests related to open issues -->\n<!--- If suggesting a new feature or change, please discuss it in an issue first -->\n<!--- If fixing a bug, there should be an issue describing it with steps to reproduce -->\n<!--- Please link to the issue here: -->\n\n### Motivation and Context\n\n<!--- Why is this change required? What problem does it solve? -->\n\n### How Has This Been Tested?\n\n<!--- Please describe in detail how you tested your changes. -->\n<!--- Include details of your testing environment, and the tests you ran to -->\n<!--- see how your change affects other areas of the code, etc. -->\n\n### Types of changes\n\n<!--- What types of changes does your code introduce? Put an `x` in all the boxes that apply: -->\n\n- [ ] Updated docs / Refactor code / Added a tests case (non-breaking change)\n- [ ] Bug fix (non-breaking change which fixes an issue)\n- [ ] New feature (non-breaking change which adds functionality)\n- [ ] Breaking change (fix or feature that would cause existing functionality to change)\n\n### Checklist:\n\n<!--- Go over all the following points, and put an `x` in all the boxes that apply. -->\n<!--- If you're unsure about any of these, don't hesitate to ask. We're here to help! -->\n\n- [ ] My code follows the code style of this project.\n- [ ] My change requires a change to the documentation.\n- [ ] I have updated the documentation accordingly.\n- [ ] I have read the **CONTRIBUTING** document.\n- [ ] I have added tests to cover my changes.\n- [ ] All new and existing tests passed.\n- [ ] I have updated the changelog."
  },
  {
    "_id": "64f327232a1079c11a9a6472",
    "title": "opensource-preset",
    "repoName": "josephguillaume/hydromad",
    "repoUrl": "https://github.com/josephguillaume/hydromad",
    "content": "#### All Submissions:\n\n* [ ] Have you followed the guidelines in our **CONTRIBUTING** document?\n* [ ] Have you checked to ensure there aren't other open [Pull Requests](../../../pulls) for the same update/change?\n\n<!-- Does this resolve or supercede an open Issue or Pull Request?\nIf so, write a line like Closes #12345 for each Issue or PR number that should be closed\nif this Pull Request is merged. -->\n\nCloses #xxxxx\n\n<!-- You can erase any parts of this template not applicable to your Pull Request. -->\n\n\n<!-- These have been added according to the rOpenSci guidelines. -->\n<!-- From: https://www.talater.com/open-source-templates/#/page/99 -->\n\n### Types of changes\n<!--- What types of changes does your code introduce? Put an `x` in all the boxes that apply: -->\n- [ ] Bug fix (non-breaking change which fixes an issue. List the bug ID if applicable)\n- [ ] New feature (non-breaking change which adds functionality)\n- [ ] Breaking change (fix or feature that would cause existing core functionality to change) \n\n\n#### New Feature Submissions checklist:\n<!--- Go over all the following points, and put an `x` in all the boxes that apply. -->\n<!--- If you're unsure about any of these, don't hesitate to ask. We're here to help! -->\n1. [ ] Have you ensured there are no conflicts with major packages (e.g. tidyverse, MASS) or base R packages?\n2. [ ] Does your new feature require documentation, and if so, have you updated the documentation?\n3. [ ] Have you added tests for your features, and do your features pass all tests?\n4. [ ] Have you linted your code with lintr locally prior to submission?\n5. [ ] Have you styled your code with styler locally prior to submission?\n6. [ ] Have you [benchmarked](https://www.alexejgossmann.com/benchmarking_r/) the performance of your code if applicable (e.g. with microbenchmark)?\n7. [ ] Does your new feature comply with existing model APIs (e.g. for models, optimisation algorithms, objective functions)?\n\n\n#### Changes to Core Features:\n<!--- Go over all the following points, and put an `x` in all the boxes that apply. -->\n<!--- If you're unsure about any of these, don't hesitate to ask. We're here to help! -->\n* [ ] Have you added an explanation of what your changes do and why you'd like us to include them?\n* [ ] Have you added tests for your core features and do your core features pass all tests?\n* [ ] Have you successfully run tests with your changes locally?\n* [ ] Does your code run on all major platforms (Windows, macOS, Linux)?\n* [ ] Have you demonstrated backwards compatibility and compatibility with the current development version, or discussed a potential break in backwards compatibility?\n* [ ] Have you updated the package vignettes? "
  },
  {
    "_id": "64f327a82a1079c11a9a6473",
    "title": "todo-preset",
    "repoName": "getlago/lago",
    "repoUrl": "https://github.com/getlago/lago",
    "content": "### Pull Request template\n\nPlease, go through these steps before you submit a PR.\n\n1. Make sure that your PR is not a duplicate.\n2. If not, then make sure that:\n\n   a. You have done your changes in a separate branch. Branches MUST have descriptive names that start with either the `fix/` or `feature/` prefixes. Good examples are: `fix/signin-issue` or `feature/issue-templates`.\n\n   b. You have a descriptive commit message with a short title (first line).\n\n   c. You have only one commit (if not, squash them into one commit).\n\n   d. `npm test` doesn't throw any error. If it does, fix them first and amend your commit (`git commit --amend`).\n\n3. **After** these steps, you're ready to open a pull request.\n\n   a. Give a descriptive title to your PR.\n\n   b. Describe your changes.\n\n   c. Put `closes #XXXX` in your comment to auto-close the issue that your PR fixes (if such).\n\n   d. Add the corresponding labels to your pull request (ex: feature, improvement, bug...)\n\nIMPORTANT: Please review the [CONTRIBUTING.md](../CONTRIBUTING.md) file for detailed contributing guidelines.\n\n**PLEASE REMOVE THIS TEMPLATE BEFORE SUBMITTING**"
  },
  {
    "_id": "64f3285f2a1079c11a9a6474",
    "title": "checklist-preset",
    "repoName": "idyll-lang/idyll",
    "repoUrl": "https://github.com/idyll-lang/idyll",
    "content": "- **Please check if the PR fulfills these requirements**\n\n* [ ] Tests for the changes have been added (for bug fixes / features)\n* [ ] Docs have been added / updated (for bug fixes / features)\n\n- **What kind of change does this PR introduce?** (Bug fix, feature, docs update, ...)\n\n* **What is the current behavior?** (You can also link to an open issue here)\n\n- **What is the new behavior (if this is a feature change)?**\n\n* **Does this PR introduce a breaking change?** (What changes might users need to make in their application due to this PR?)\n\n- **Other information**:"
  }
]
```

### /file/pr/\<id>

#### Response Body

```plain
- **Please check if the PR fulfills these requirements**

* [ ] Tests for the changes have been added (for bug fixes / features)
* [ ] Docs have been added / updated (for bug fixes / features)

- **What kind of change does this PR introduce?** (Bug fix, feature, docs update, ...)

* **What is the current behavior?** (You can also link to an open issue here)

- **What is the new behavior (if this is a feature change)?**

* **Does this PR introduce a breaking change?** (What changes might users need to make in their application due to this
PR?)

- **Other information**:
```

### /file/contributing

#### Response Body

```json
[
  [
    {
      "_id": "64ed7ca9c7efe914a8d14a4f",
      "type": "0.Welcome",
      "title": "Welcome to Open-Set-Go contributing guide",
      "repoName": "AgainIoT/Open-Set-Go",
      "repoUrl": "https://github.com/AgainIoT/Open-Set-Go",
      "content": "# Welcome to Open-Set-Go contributing guide\n\nThank you for investing your time in contributing to our Open-Set-Go project! Any contribution you make will be reflected on [Open-Set-Go.io](https://open-set-go.netlify.app/) & [README.md](https://github.com/AgainIoT/Open-Set-Go#contributors) ✨.\n\nWe are committed to fostering a contribution-friendly environment that encourages contributions and aims to evolve into an open-source community. Please have a lot of conversations on [our Discussion](https://github.com/AgainIoT/Open-Set-Go/discussions)!\n\nIn this guide you will get an overview of the contribution workflow from opening an issue, creating a PR, reviewing, and merging the PR.\n<br>"
    },
    {
      "_id": "64ed7cf5c7efe914a8d14a50",
      "type": "0.Welcome",
      "title": "Welcome to GitHub docs contributing guide",
      "repoName": "github/docs",
      "repoUrl": "https://github.com/github/docs",
      "content": "# Welcome to GitHub docs contributing guide <!-- omit in toc -->\n\nThank you for investing your time in contributing to our project! Any contribution you make will be reflected on [docs.github.com](https://docs.github.com/en) ✨.\n\nRead our [Code of Conduct](./CODE_OF_CONDUCT.md) to keep our community approachable and respectable.\n\nIn this guide you will get an overview of the contribution workflow from opening an issue, creating a PR, reviewing, and merging the PR.\n\nUse the table of contents icon <img src=\"https://github.com/github/docs/raw/main/contributing/images/table-of-contents.png\" width=\"25\" height=\"25\" /> on the top left corner of this document to get to a specific section of this guide quickly."
    }
  ],
  [
    {
      "_id": "64ee1bca9dede57491a7c180",
      "type": "1.Ways to contribute",
      "title": "Ways to contribute by Open-Set-Go",
      "repoName": "AgainIoT/Open-Set-Go",
      "repoUrl": "https://github.com/AgainIoT/Open-Set-Go",
      "content": "## Ways to contribute\n\n### Contributors\n\nThere are several ways you can contribute to Open-Set-Go!\n\n- Troubleshoot problems that existed code.\n- Submit Bug/Feature issues related to [bugs](https://github.com/AgainIoT/Open-Set-Go/issues?q=is%3Aopen+is%3Aissue+label%3Abug) or desired [new features](https://github.com/AgainIoT/Open-Set-Go/issues?q=is%3Aopen+is%3Aissue+label%3Afeature-request).\n- Submit Documentation issues for insufficient documents, translations.\n- Start conversation at [Discussions](https://github.com/AgainIoT/Open-Set-Go/discussions) to provide a good example of preset.\n- Start conversation by posting to [Discussions](https://github.com/AgainIoT/Open-Set-Go/discussions) about a framework that needs support.\n- If there's anything you'd like to communicate about our project or open source, feel free to post it on [Discussions](https://github.com/AgainIoT/Open-Set-Go/discussions)! _\"We hope that **Open-Set-Go Discussions** will become an active community.\"_\n\n### Collaborators\n\nIf you want to contribute directly to our project, be our collaborators at Open-Set-Go! Join the [Slack](https://join.slack.com/t/open-set-go/shared_invite/zt-21jwlzs9g-qrajfUblcCtmCqAy0Xxj8w) to become a collaborator!\n\n- **Develop Main Features**: <br>\n  Collaborator will develop the main features with maintainers based on milestone\n  All contributions are equally valuable and valuable to Open-Set-Go projects.and issues.\n\n- **Communication**: <br>\n  Communicate with Open-Set-Go maintainers with [Slack](https://join.slack.com/t/open-set-go/shared_invite/zt-21jwlzs9g-qrajfUblcCtmCqAy0Xxj8w) to carry out the project.\n\n<br>\n\n> All contributions are equally valuable and valuable to Open-Set-Go projects.\n\n<br>"
    }
  ]
]
```

### /file/readme/\<id>

#### Response Body

```plain
## Welcome to Open-Set-Go contributing guide

Thank you for investing your time in contributing to our Open-Set-Go project! Any contribution you make will be
reflected on [Open-Set-Go.io](https://open-set-go.netlify.app/) &
[README.md](https://github.com/AgainIoT/Open-Set-Go#contributors) ✨.

We are committed to fostering a contribution-friendly environment that encourages contributions and aims to evolve into
an open-source community. Please have a lot of conversations on [our
Discussion](https://github.com/AgainIoT/Open-Set-Go/discussions)!

In this guide you will get an overview of the contribution workflow from opening an issue, creating a PR, reviewing, and
merging the PR.
<br>
```

### /file/readme/\<id>

#### Response Body

```json
[
  {
    "_id": "64ed835fc7efe914a8d14a51",
    "type": "welcome",
    "title": "title1",
    "repoName": "test1",
    "repoUrl": "www.google.com",
    "content": "content1"
  },
  {
    "_id": "64ed838ac7efe914a8d14a52",
    "type": "welcome",
    "title": "title2",
    "repoName": "test2",
    "repoUrl": "www.google.com",
    "content": "content2"
  }
]
```

### /file/contributing/\<id>

#### Response Body

```plain
content1
```

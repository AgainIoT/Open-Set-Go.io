---
title: "Commands For Server"
description: ""
lead: ""
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "guideForDevelopment"
weight: 180
toc: true
---

{{< alert icon="💡" text="You can check the command in the Script section of '/package.json'." />}}

## Build

Build project:

```bash
yarn build
```

## Start

Command to Execute:

```bash
yarn start
```

Instructions that can be executed immediately and watch the results immediately:

```bash
yarn start:dev
```

## Lint

Check scripts, styles, and markdown for errors:

```bash
yarn lint
```

### Deploy

Deploy project:

```bash
yarn deploy
```

### CI

Code Style Verification (code commitment only when passing CI):

```bash
yarn CI
```

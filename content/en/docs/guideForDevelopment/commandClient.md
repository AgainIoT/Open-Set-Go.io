---
title: "Commands For Client"
description: ""
lead: ""
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "guideForDevelopment"
weight: 190
toc: true
---
{{< alert icon="💡" text="You can check the command in the Script section of '/package.json'." />}}

## Start

Command to Execute:

```bash
yarn start
```

Start HTTPS for linux:

```bash
yarn start:linux
```

Start HTTPS for windows:

```bash
yarn start:wins
```

## Build

Build project:

```bash
yarn build
```

Installs serve package:

```bash
yarn global add serve
```

Serve your build directory:

```bash
serve -s build
```


## CI

Code Style Verification (code commitment only when passing CI):

```bash
yarn CI
```
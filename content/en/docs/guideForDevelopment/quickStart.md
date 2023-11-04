---
title: "Quick Start"
description: "One page summary of how to start a Open-Set-Go project."
lead: "One page summary of how to start a Open-Set-Go project."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "guideForDevelopment"
weight: 120
toc: true
---

### 🙎 Client

1.**Install with script**

You can also easily install it through [install.sh](https://github.com/AgainIoT/Open-Set-Go#installation--development-environment)!

2.**Install Manually**

- Clone our Repository!

  ```bash
  git clone https://github.com/AgainIoT/Open-Set-Go_client.git
  ```

- Install the Development Environment

- Install Node Dependencies

  ```bash
  yarn install
  ```

- Create `.env` file at root to use secret environment

  > See more details at [EnvironmentVariable.md](https://github.com/AgainIoT/Open-Set-Go/blob/main/EnvironmentVariable.md)

- Start Open-Set-Go Server

   ```bash
    # for development
    yarn start
    yarn start:linux # start HTTPS for linux
    yarn start:wins # start HTTPS for windows

    # for production
    yarn build
    yarn global add serve
    serve -s build
   ```

### 🖥️ Server

1.**Install with script**

You can also easily install it through [install.sh](https://github.com/AgainIoT/Open-Set-Go#installation--development-environment)!

2.**Install with docker**

- Pull our docker image!

  ```bash
   docker pull ymw0407/open-set-go_server
  ```

- Create `.env` file at root to use secret environment

  > See more details at [EnvironmentVariable.md](https://github.com/AgainIoT/Open-Set-Go/blob/main/EnvironmentVariable.md)

- Start Open-Set-Go Server's docker with environment variable!

  2.**Install Manually**

- Clone our Repository!

  ```bash
  git clone https://github.com/AgainIoT/Open-Set-Go_server.git
  ```

- Install the Development Environment

- Install Node Dependencies

  ```bash
  yarn install
  ```

- Create `.env` file at root to use secret environment

  > See more details at [EnvironmentVariable.md](https://github.com/AgainIoT/Open-Set-Go/blob/main/EnvironmentVariable.md)

- Start Open-Set-Go Server

   ```bash
    # for development
    yarn start
    yarn start:dev # Restart by detecting changes in the file!

    # for production
    yarn build
    node dist/main.js
   ```

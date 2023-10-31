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

### 🖥️Server

**Install with script**

You can also easily install it through [install.sh](https://github.com/AgainIoT/Open-Set-Go#installation--development-environment)!

**Install with docker**

1. Pull our docker image!

   ```
    docker pull ymw0407/open-set-go_server
   ```

2. Create `.env` file at root to use secret environment

   > See more details at [EnvironmentVariable.md](https://github.com/AgainIoT/Open-Set-Go/blob/main/EnvironmentVariable.md)

3. Start Open-Set-Go Server's docker with environment variable!

**Install Manually**

1. Clone our Repository!

   ```bash
   git clone https://github.com/AgainIoT/Open-Set-Go_server.git
   ```

2. Install the Development Environment

3. Install Node Dependencies
   ```bash
   yarn install
   ```
4. Create `.env` file at root to use secret environment

   > See more details at [EnvironmentVariable.md](https://github.com/AgainIoT/Open-Set-Go/blob/main/EnvironmentVariable.md)

5. Start Open-Set-Go Server

   ```bash
     # for development
     yarn start
     yarn start:dev # Restart by detecting changes in the file!

     # for production
     yarn build
     node dist/main.js
   ```

### 🙎Client

**Install with script**

You can also easily install it through [install.sh](https://github.com/AgainIoT/Open-Set-Go#installation--development-environment)!

**Install Manually**

1. Clone our Repository!

   ```bash
   git clone https://github.com/AgainIoT/Open-Set-Go_client.git
   ```

2. Install the Development Environment

3. Install Node Dependencies
   ```bash
   yarn install
   ```
4. Create `.env` file at root to use secret environment

   > See more details at [EnvironmentVariable.md](https://github.com/AgainIoT/Open-Set-Go/blob/main/EnvironmentVariable.md)

5. Start Open-Set-Go Server

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
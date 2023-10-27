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

**<li> Clone our Repository**

```bash
git clone --recursive https://github.com/AgainIoT/Open-Set-Go_server.git

######################################
# Open-Set-Go Repository Dependencies
#
# Open-Set-Go_server
#  ┗ environment-template
#
######################################
```

**<li> Install the Development Environment**

**<li> Install Node Dependencies**

```bash
yarn install
```

**<li> Create your own github-oauth app**

Follow the [GitHub Docs](https://docs.github.com/ko/apps/oauth-apps/building-oauth-apps/creating-an-oauth-app) to get Client ID & Client Secret.<br>
If your Authorization URL should be `localhost:3000` !

**<li> Create `.env` file at root to use secret environment**

```bash
touch .env
```

**<li> Fill in the `.env` file as follows**

```bash
MONGODB_URI="<Your-MongoDB-URI-start-with-mongodb://>"
CLIENT_ID="<Your-GitHub-OAuth-Client_ID>"
CLIENT_SECRET="<Your-GitHub-OAuth-Client_Secret>"
JWT_SECRET="<Any-JWT-Secret-You-Want>"
JWT_EXPIRATION_TIME="<JWT-Expiration-Time-You-Want-default-18000>"
```

**<li> Start Open-Set-Go Server**

```bash
  yarn start
```

### 🙎Client

**<li> Clone our Repository**

```bash
git clone https://github.com/AgainIoT/Open-Set-Go_client.git

######################################
# Open-Set-Go Repository Dependencies
#
# Open-Set-Go_client
#
######################################
```

**<li> Install the Development Environment**

**<li> Install Node Dependencies**

```bash
  yarn install
```

**<li> Create your own github-oauth app**

Follow the [GitHub Docs](https://docs.github.com/ko/apps/oauth-apps/building-oauth-apps/creating-an-oauth-app) to get Client ID & Client Secret.<br>
If your Authorization URL should be `localhost:3000` !

**<li> Create `.env` file at root to use secret environment**

```bash
touch .env
```

**<li> Fill in the `.env` file as follows**

```bash
REACT_APP_CLIENT_ID="<Your-GitHub-OAuth-Client_ID>"
REACT_APP_REDIRECT_URL="http://localhost:3000/login"
REACT_APP_SERVER_URL="http://localhost:8080"
```

**<li> Start Open-Set-Go Server**

```bash
yarn start
```

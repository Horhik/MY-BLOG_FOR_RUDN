---
title: Instagram2Fedi
summary: Python script for crossposting from Instagram to Mastodon or Pixelfed 
tags:
  - Code
date: '2021-04-27T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
  - icon: github
    icon_pack: fab
    name: GitHub
    url: https://github.com/Horhik/Instagram2Fedi
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example
---


_Guys... Instagram is sh*t. Even [bibliogram](https://www.reddit.com/r/privacy/comments/wrczxc/bibliogram_is_being_discontinued/) is being discontinued. If you're able to migrate you proile to any fediverse instance or contact to person, whose instagram you'd like to crosspost and ask him to post to fediverse to, it wil be the best desicion_

# Instagram2Fedi <span><img width="50px" src="https://upload.wikimedia.org/wikipedia/commons/9/93/Fediverse_logo_proposal.svg"></span>

Simple tool for crossposting posts from instagram to Mastodon/Pixelfed.

## Using without docker
See [Docs.md](./Docs.md)

## Using docker-compose

1. create `docker-compose.yaml` with following content
_You can use default.docker-compose.yaml from repo_
``` yaml
version: '3'
services:
  bot:
    build:
      context: .
    image: "horhik/instagram2fedi:latest"
    environment:
      - YOUR_CONTAINER_NAME=<whatever>
      - I2M_INSTAGRAM_USER=<instgram username>
      - I2M_INSTANCE=<mastodon or pixelfed instance>
      - I2M_TOKEN=<your token here>
      - I2M_CHECK_INTERVAL=3600 #1 hour    
      - I2M_POST_INTERVAL=3600 #1 hour   
      - I2M_USE_MASTODON=4 #max carouse    - is 4, if there's no limit set to -1
      - I2M_FETCH_COUNT=5 # how many instagram posts to fetch per check_interval   -
      - I2M_USER_NAME=admin # Your instagram login name
      - I2M_USER_PASSWORD=admin # Your instagram password
```

** Note: ** _Since somewhen it's seems not possible to fetch any data from instagram anonymously (maybe i'm wrong and there's a solution, I'll be very happy to know about it). Due that you unfortunately have to had an instagram accound and provide login and password to this script_

2. And edit environment variables

3. Run `docker-compose up -d`


## Using with Dockerfile

Just clone repo, specify variables and run it.
You can write all needed variables in `./env.sh` and then do `source ./run.sh`

``` bash
git clone https://github.com/horhik/instagram2fedi
cd instagram2fedi
nano ./env.sh
source ./run.sh
```


![screenshot](./img.png)





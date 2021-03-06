# Timezone

> **Note** For the repo for the SaaS app **[Timezone.io](http://timezone.io)** 
head over to **[timezoneio/timezoneio](https://github.com/timezoneio/timezoneio)**.
This project is the original, simple version meant to be self-hosted. Please
feel free to sign up for free at **[Timezone.io](http://timezone.io)** and 
contribute issues and pull requests on that project's repo!

Timezone is an application aimed at helping remote teams by making it easier
to see where and **when** their coworkers are. This project was the basis for 
the larger [Timezone.io](https://github.com/timezoneio/timezoneio) project and
is meant for self-hosting.

![Screenshot](https://dl.dropboxusercontent.com/u/50627698/timezone-github.png)

# Setup

Clone this repo and add a `people.json` file in the repo's
`data` directory.  Timezone codes for the `tz` field can be found
[here](http://momentjs.com/timezone/).

Each person object should have data in the following format:

```json
[
  {
    "name": "Dan",
    "avatar": "https://d389zggrogs7qo.cloudfront.net/images/team/dan.jpg",
    "city": "NYC",
    "tz": "America/New_York"
  },
  {
    "name": "Niel",
    "avatar": "https://d389zggrogs7qo.cloudfront.net/images/team/niel.jpg",
    "city": "Cape Town",
    "tz": "Africa/Johannesburg"
  }
]
```

# Configuration

By default, timezone uses port 3000.  This port can be changed by setting
the environment variable, `PORT`.  i.e. `PORT=80` to use port 80.

# Deploy

This project is easily deployable on both Heroku and via docker.

## Heroku

This project is designed with a Procfile to deploy to a Heroku
instance. Please check with Heroku's up to date documentation for any
latest changes. You should be able to commit your changes in your forked
repo (including adding your own people.json file) then run:

```bash
  $ heroku create
  $ git push heroku master
```
## Docker

With docker, build the image with the following command:

```bash
  $ docker build -t timezone .
```

You can run the command as follows:

```bash
  $ docker run -d -p 3000:3000 -v $PWD:/usr/src/app/data --name timezone timezone
```

**Note:** the `-p`, `-v` and `--name` argument are optional.  `-v`
can be used to mount a directory with the `people.json` file.

# Development

You must have [Node.js](http://nodejs.org/) and [Browserify](http://browserify.org/)
installed on your system to compile the project assets. After install Node.js, run:

```bash
  $ npm install -g browserify
```

To run the server and download all dependencies for the project run this in the
project root directory:

```bash
  $ npm install
```

`bundle.js` contains all of the necessary scripts and data for the client.
To re-build this file with Browserify run:

```bash
  $ npm run build
```

Now to start the server on localhost:3000 you can run:

```bash
  $ node ./index.js
```

**Note:** These docs are very basic and need some more love. I'll add more info
soon  :)

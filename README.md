# Docker dev environment for Reveal.js

The aim of this repository is to provide a demonstration on how
to create a Docker dev environment which allows to run a reveal.js
presentation.

The [`.docker/Dockerfile.devenv`](.docker/Dockerfile.devenv) clones
reveal.js in the `/work` directory and creates a `/work/slides` simlink (`ln -s`)
which points to `/com.docker.devenvironments.code`. The later is the directory
in which the git repository will be mounted. The [`.docker/index.html`](.docker/index.html)
automatically redirects (using javascript) the `http://localhost:8080/` request to
the `/slides` sub directory.

## Usage

Create a new Docker dev environment (in the Docker Desktop UI) based
on this repository. Open the remote environment in VSCode and then a
termnial. Switch to the `/work` directory then run the command
`npm start`. This trick allows to server the [`index.html`](index.html)
directly as if it was at the root of the web server.

The presentation should be available at [http://localhost:8000](http://localhost:8000)

## Limitations

* The live reload of the presentation does not work. It is however
  possible to reload the presentation manually.
* In order to install custom reveal.js plugins, it is required to 
  modify the image definition [`.docker/Dockerfile.devenv`](.docker/Dockerfile.devenv).

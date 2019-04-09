# EAO

## Important: Branch & Pull Request Workflow

Please use the following steps for working on this project:

* Fork this repo
* Clone your fork to your local machine
* Go into branch master
* Set up your upstreams

```bash
git remote add upstream https://github.com/bcgov/eao-inspections-web.git
git fetch upstream
```

* Create a branch for your work
* Checkin, commit, push to origin
* Create a PR

Reviewers and maintainers - DO NOT MERGE the PR via GitHub, let the pipeline do this.  DO NOT manually clean up branches, let the pipeline do this.  Doing either of these manually will break the pipeline and cause all kinds of problems.

Also, be AWARE: if Jenkins reboots while partially through the pipeline, the input stages will be permanently broken and the job will need to be cancelled and re-run in order for the inputs to work again.

Here are the steps to follow:

* Go into the tools environment in OpenShift
* Find the Jenkins deployment and click on the URL route upper right of the deployment
* Authenticate to Jenkins
* Find the PR (the BlueOcean view is nice)
* There are several stages to go through so make sure you do not skip any
* Approve or Cancel each stage (you may need to exit the page and reload in order to see the next input prompt)
* If you approve going out to prod, don't forget to approve the final cleanup stage

This will get your changes to the correct environments and dispose branches and resources properly.

## About

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.6.6.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).


# ------------------------------------------------------------------------------
# Freshworks Deployment Process
# ------------------------------------------------------------------------------

[Project Creation---- ----------------------------------------------------------]

- oc login ::REPOSITORY:: [--token=::TOKEN::]
- oc new-project ::POJRECT_NAME::
- ensure .env, Dockerfile and src/environments are setup
- make ::dev|prod:: new-app


[Local Development]

- ng serve
- (or) make local (if you need to run on Docker image. Can shell into the container by ::make workspace::) 


[ Deployments ]

- ensure that the app has been created and all configuration is setup
- oc status ( confirm before deploy ! )
- oc get routes ( confirm before deploy ! )

- make ::dev|prod:: deploy


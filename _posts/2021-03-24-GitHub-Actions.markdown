---
layout: post
title:  "Getting started with GitHub Actions"
description: "How to set up github actions"
date:   2021-03-24 12:03:42 +0300
categories: jekyll update
---

Github Actions helps you create custom workflows during software development directly in your Github repository. These workflows are made out of different actions(tasks) that can be run automatically on certain events.

This enables you to include Continues Integration (CI) and continuous deployment (CD) capabilities and many other features directly in your repository.

## CI/CD
Continuous Integration(CI) and Continuous Deployment(CD) are modern methods in the Software development cycle that reduce on the repitive tesing and deployment of software. GitHub actions is one of the simplest ways to implement CI and CD.

#### Continuous Integration (CI)
Continuous integration (CI) is a software development practice that requires frequently committing code to a repository. Committing code usually detects errors faster and reduces the amount of code to debug when finding the source of an error. 

#### Continuous Deployment (CD)
Continuous Deployment(CD) is a practice used to automatically publish a site that has its most recent changes submitted to Continuous integration tests. If the tests are passed, the changes are reflected in the published site. 

## Understanding Workflows/ Action files
A Workflow is an automated process that is made up of one or multiple jobs and can be triggered by an event. Workflows are defined using a YAML file in the .github/workflows directory.

#### Setting up workflows
GitHub marketplace provides some workflow and action templates for users. This is one of the easiest ways to set up workflows on GitHhub actions.

## Adding a workflow template
* You can use one of the templates suggested by GitHub or write your own from sratch. Use the suggested templates if you're not sure of which actions to use. To add a workflow template, navigate to the <mark>Actions</mark> tab on the main page of your repository.
![Workflow template](/assets/images/action_template.png)
* Pick a template you would like to use then click **Set up this workflow**   

## Adding an action template
* You can also add an action template by checking the GitHub Marketplace on the far right of the workflow template. 
![Action template](/assets/images/marketplace.png)
* Add the template you choose by copying its code and pasting it in the .yml file.
![Action template details](/assets/images/action_template_details.png) 

## Creating a workflow file
* Create a workflow file by adding a .yml file in the <mark>.github/workflows</mark> directory.
* Here is an explained sample action file
{% highlight ruby %}
name: Ruby

on:
  push:
    branches: 
    - master
  pull_request:
    branches: [ master ]

jobs:
  ruby:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - uses: helaili/jekyll-action@2.0.1
    env:
          JEKYLL_PAT: ${{ secrets.JEKYLL_PAT }}
{% endhighlight %}

* **name** is the name of the workflow displayed on the Github actions page.
* The keyword **on** defines the GitHub events that trigger the workflow.
* A **job** is made up of multiple steps that define the functionality that will be run in the workflow. The name of the job has to match the name of the yml file.
* The **runs on** keyword helps you specify the Operating Sysytem on which your job runs.
* The **checkout action** is in charge of cloning the repository.
* **helaili/jekyll-action@[VERSION]** specifies action and version number that handles the build and deploy.
* **env** defines environment variables that are available to all jobs and steps in the workflow.

# Using Secrets to build the site
- To build using secrets, you need to generate a token on your github profile and set it as an envireonment variable.
    * Go to your *Profile Settings* and select **Developer Settings**
    * Select *Personal Access Token* and generate a  new token with an appropriate name.
    * Ensure to check the *repo* checkbox to give access to the entire repository.
    * Copy the token value that is to be used later.
    * From there, go to your repository settings and select Secrets.
    * Give the secret an apporpriate name to be used to reference data in the workflow.
    * Paste the token value in the value of the secret
    * To use the secret, go to the workflow yml file and reference it using the secrets context.

Congrats! You have now set up GitHub Actions successfully. From here any changes made to the master branch will trigger an action and the build will start. This action can be monitored from the actions tab of your repository. Any further changes commited and pushed to master re-run the work flow and trigger the action again, causing the build to automatically restart.
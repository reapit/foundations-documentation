---
description: A Command Line Interface tool for interfacing with Reapit's IaaS platform
---

# 💻 CLI (Beta)

The Command Line Interface tool will enable Reapit customers to create, build, configure, deploy, rollback and manage deployments to the Reapit IaaS Platform.

### Installing

With NodeJS installed, use npm or yarn to install the Reapit CLI tool globally.

```bash
$ npm i -g @reapit/cli
```

### Configure the CLI

First visit the developer portal and load any app page. Visit the pipelines page, and on the left hand side click the "API Keys" button to open a modal window. Click "Create API Key" and copy the result to your clipboard. You can add multiple API keys from this view and delete them as required.

![](<../../.gitbook/assets/Screenshot 2022-06-17 at 12.46.49.png>)

Once you've obtained an api-key. You can set this up with the Reapit Cli by running:

```bash
$ reapit config
```

This command will then prompt you for the input of your api-key

{% hint style="info" %}
When prompted about what type of config to make. Choose global for general projects. Project Reapit config is designed for multiple Reapit accounts.
{% endhint %}

Just to make sure you've got your api-key setup and ready to go, run the `reapit config` command again and choose `show` to see your currently set config.

### Bootstap React App

Get started building your react app as quickly as possible by using the Reapit Bootstrap app to create your React App in your current working directory, complete with all the tooling from our Create React App template.

```
$ reapit bootstrap my-new-reapit-app react {client-id} {user-pool}
```

{% hint style="info" %}
Make sure to add the client-id from your app and the required user-pool
{% endhint %}

### Bootstrap Node App (coming soon)

This command will be used to generate a node web application to be used with our IaaS platform. Not currently supported but on our roadmap.

### Pipeline Commands

The CLI supports a number of commands to manage a pipeline for your application.

#### List Pipelines

Run the below command to see a list of pipelines that are currently authorised for your given api-key.

```
$ reapit pipeline list
```

#### Create a Pipeline

Use the below command to start creating a pipeline. The Reapit CLI will then prompt you for required options and configurations.

```
$ reapit pipeline create
```

Required options you will be asked for

* App Id
* Project Name
* Deployment Branch (from your repository)
* App Type (react or node)
* Repository url (a default url will be supplied if a repository is found in cwd)
* OutDir (your application's build directory)
* Build Command (the command used to build your application)
* Package Manager (yarn or npm)

This command will then give you live updates of the IaaS platform creating your pipeline and the current state as it provisions your pipeline.

#### Editing Pipeline Config

This commands allows you to update the reapit pipeline config which will then sync with our IaaS platform.

```
$ reapit pipeline edit
```

#### Link an existing Pipeline

Pipelines can be automatically created when creating an app. This command allows you to download an existing pipeline's configuration in your current working directory.

```
reapit pipeline link {pipeline-id}
```

#### Delete Pipeline

Simply run the below command when in the directory with the Reapit pipeline config file output at the pipeline create stage.

```
reapit pipeline delete
```

### Release Commands

Commands that manage and trigger the deployment of your code to our infrastructure. You will need to have configured a pipeline before releasing your code.

#### List Releases

Use the below command to list out deployments made on a pipeline within the cwd.

```
$ reapit release list
```

#### Get the Current Release

Use the below command to deploy a previously deployed version.

```
$ reapit release version
```

This command will list out the available versions for you to select one to be deployed.

#### Release from local build

This command will trigger a deployment using the pipeline's configured build directory within the current working directory. It assumes that you have previously built the application before running.

```
$ reapit release zip
```

This command will also prompt and update your package's version value with your given value.

#### Release from repo

Trigger a deployment using the below command in your app's cwd. Assumes you have the latest version of your app pushed to your configured main branch.

```
$ reapit release repo
```

This will begin a deployment which the command will then give real time updates on. This can be closed and the deployment will continue.


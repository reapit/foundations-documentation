---
description: Pipeline management within the Developer Portal
---

# 🖥 Developer Portal (Beta)

If you prefer a GUI to manage your deployments over a terminal based CLI, you can manage this from within the Developer Portal itself. When you have been enabled as part of the public beta, you will see both a top level navigation item `IaaS`, that gives you an overview dashboard of your pipelines, plus, each app has a Pipeline configuration page.

The first step to deploy an app is to visit the app detail page in the developer portal at `/apps/:id` If you are part of the beta and have pipelines enabled, you will see a new "Pipeline" menu item for your client side authenticated apps.

### Getting Started - Pre Existing Apps

For apps that pre-exist the IaaS service, this was not possible so you will see this screen:

![](<../../.gitbook/assets/Screenshot 2022-05-05 at 13.19.47.png>)

From here you should hit "Create Pipeline" to take you to the new pipeline page.

![](<../../.gitbook/assets/Screenshot 2022-05-05 at 13.21.32.png>)

From here, you need to tell us about your application, the repo (we support Github and BitBucket), the main branch, the command in your package.json that builds the app and the directory your assets are output to.

On saving this config, you have pre-provisioned an app and you will return to the Pre provisioned app screen.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 15.44.26 (1).png>)

You should now hit "Provision", to build your initial infrastructure on our services. This can take a minute or two. You can also move on to the [Next Steps](developer-portal-beta.md#next-steps-all-apps) section below.

### Getting Started - New Apps

If you created a new application, we pre-provision a Pipeline for your application by default. Visiting the "Pipeline" tab you will see this page:

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 15.27.06.png>)

Note the state of the application is "Pre provisioned". This means we have a shell pipeline and have reserved a domain name for your app in our infra. The first step is to configure your app by clicking on the "Configure" tab.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 15.41.26.png>)

From here, you need to tell us about your application, the repo (we support Github and BitBucket), the main branch, the command in your package.json that builds the app and the directory your assets are output to. Hit save config and return to the deployments page.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 15.44.26.png>)

You should now hit "Provision", to build your initial infrastructure on our services. This can take a minute or two. You can also move on to the [Next Steps](developer-portal-beta.md#next-steps-all-apps) section below.

### Next Steps - All Apps

When you have done this, if your app is on Github, you will need to install our Github App from [this page](https://github.com/apps/reapit) following the steps to configure for your repo. This gives us the permission to pull from your repo and receive webhooks that inform us when you git push to your main branch.&#x20;

For Bitbucket the process is the same but you will need to install the [dedicated app here.](https://bitbucket.org/site/addons/authorize?addon\_key=reapit)

{% hint style="info" %}
You should only install the Github / Bitbucket app for a single repo, not your whole organisation as it sets up a webhook on an app by app basis. If you delete your app or pipeline, and set up a new one for your repo, you need to uninstall and re-install the Github app each time.&#x20;
{% endhint %}

Having installed the app, you are ready to do your first build. Hit the "deploy" button.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 15.59.14.png>)

The page will start to update in live time as we pull, build and deploy your code.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 16.02.27 (2).png>)

And that's it! On completion of all the steps, you can then visit your deployed application using the Location Link.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 16.07.32.png>)

### Additional Features

#### Logs

You can view the logs of your deployment to check for any build errors. These are visible from the slide down in the deployments table you can see above. They will be in plain text form and will open in a new tab in your browser to download.

#### Deleting Pipelines

You can delete pipelines from the pipeline deployments page however, a couple of things to note.&#x20;

Firstly, it will tear down all of your current infra and delete the pipeline record. This means any testing or users that are relying on your deployment will not be able to access the url again. You can create a new pipeline but you can't specify the same location (url), as before.

Secondly, the command issues a request to delete the infra. This process is quite lengthy so you should check back after a few minutes to verify everything has been torn down. See below for an example of a pipeline in it's deletion state.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 16.51.26.png>)

#### Environment Variables

You can add your Environment variables for your application here. If you supply any key value pair we will write them to the process.ENV object at compile time when building your app.

You can then reference them in your code with the line, where `FOO` is the key of your variable.

`process.env.FOO`

All variables are stored in a secure and encrypted format however, if you are building a web app environment variables are inherently insecure. As such, you should only store values that can be exposed on the client side.

Currently we do not surface your variables over an API when you have stored them for security reasons. If you need to confirm a variable value, we would advise updating it and re-deploying your app.

See below for the Environment Variables UI:

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 17.02.36.png>)

#### API Keys

API keys are used by the Reapit CLI to authenticate against our Pipeline endpoints. You don't need them unless you intent to use the CLI. For more on this see [Configuring the CLI here](cli-beta.md#configure-the-cli)

### Pipeline Dashboard

From the top level nav you can also view the IaaS pipeline dashboard that gives you an overview of the current statuses of all your app pipelines. By expanding each row, you have quick links to the deployed app, your Pipeline config and the recent app deployments.

![](<../../.gitbook/assets/Screenshot 2022-06-16 at 16.05.15.png>)

### Troubleshooting&#x20;

We will try to update this section regularly with frequently asked questions while we are in beta.

* **My deployment fails immediately after hitting deploy.**  First check you have the Github app installed. Then check you have installed for a single repo, not your whole organisation as it sets up a webhook on an app by app basis. If you delete your app or pipeline, and set up a new one for your repo, you need to uninstall and re-install the Github app each time. Secondly check your config is correct from the "Configure" tab, specifically the repo url. Any errors in the url will mean we can't find or build your app correctly.
* **My deployment fails at one of the build steps.** This is likely because of an issue building you app itself. Check the download logs button in the expandable pipeline table row for build errors and check if you can replicate locally. Also check your config to ensure the build directory, build task and package manager are correct. Any errors here can cause build issues.
* **My app deployed but I see a re-direct mismatch error when first clicking on the link.** We update your app re-direct uris when provisioning a pipeline however, if this fails you may need to update them manually to the location of your deployed app from the `apps/:id/edit` page,  authentication tab. Also, check the client id for your app is the correct one for your pipeline. Redirect URIs are specific to client ids so must match the data we hold on your app.

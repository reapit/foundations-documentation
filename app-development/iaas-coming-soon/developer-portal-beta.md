---
description: Pipeline management within the Developer Portal
---

# 🖥 Developer Portal (Beta)

If you prefer a GUI to manage your deployments over a terminal based CLI, you can manage this from within the Developer Portal itself. When you have been enabled as part of the public beta, you will see both a top level navigation item `IaaS`, that gives you an overview dashboard of your pipelines, plus, each app has a Pipeline configuration page.

### Getting Started

The first step to deploy an app is to visit the app detail page in the developer portal at `/apps/:id` If you are part of the beta and have pipelines enabled, you will see a new "Pipelines" menu item for your client side authenticated apps.

When you create a new application, we pre-provision a Pipeline for your application by default. For apps that pre-exist the IaaS service, this was not possible so you will see this screen:

![](<../../.gitbook/assets/Screenshot 2022-05-05 at 13.19.47.png>)

From here you should hit "Create Pipeline" to take you to the new pipeline page.

![](<../../.gitbook/assets/Screenshot 2022-05-05 at 13.21.32.png>)

From here, you need to tell us about your application, the repo (we support Github and BitBucket), the main branch, the command in your package.json that builds the app and the directory your assets are output to.

On saving this config, you have pre-provisioned an app and you will see the following screen.&#x20;

![](<../../.gitbook/assets/Screenshot 2022-05-05 at 13.25.15.png>)

At this point, you should visit the configure tab, to  complete the build details, in the same format as the "New Pipeline" page above.

When you have done this, if your app is on Github and private, you will need to install our Github App from this page: [https://github.com/apps/reapit](https://github.com/apps/reapit) following the steps to configure for your repo. This gives us the permission to pull from your private repo.

Having installed the app, you are ready to do your first build. Hit the "provision" button and the page will start to update in live time as we pull, build and deploy your code.

![](<../../.gitbook/assets/Screenshot 2022-05-05 at 13.30.02.png>)

And that's it! On completion of all the steps, you can then visit your deployed application using the Location Link.

### Pipeline Dashboard

From the top level nav you can also view the IaaS pipeline dashboard that gives you an overview of the current statuses of all your app pipelines. By expanding each row, you have quick links to the deployed app, your Pipeline config and the recent app deployments.

![](<../../.gitbook/assets/Screenshot 2022-05-05 at 14.26.35.png>)


---
description: Infrastructure As A Service platform
---

# IaaS (Coming Soon)

### Introduction

Infrastructure As A Service (IaaS). The Reapit IaaS is a platform for Reapit customers to host their applications.

Reapit Developers can host their React applications (Node apps coming soon), on Reapit's hosting, saving your developers time in setting up these solutions themselves.

You will soon be able to build and deploy fully functional Reapit Apps both on the front end and back end offering full functionality of the Reapit Platform for any requirement.\
\
Think of Reapit IaaS as CI/CD pipeline for your Reapit applications that also includes hosting.

### Public Beta

The IaaS services are part of a public beta that needs to be enabled by one of our team for your Developer Organisation.  If you are interested in trialing this service, please drop us a line at [**iaasbeta@reapitfoundations.zendesk.com**](mailto:iaasbeta@reapitfoundations.zendesk.com) **** to join the waiting list.

We will be inviting developer organisations in slowly while we scale up the infrastructure required to power the service so please be aware, whilst we will confirm your interest right away, it may take some time to get you live.&#x20;

Please also be aware that whilst the service is free in Beta, charges will apply when the service goes to full production. We will advise you in advance of this prior to any charges being incurred.

### Features

#### Hosting

The Reapit IaaS Platform offers hosting for your JavaScript single page application in our AWS infrastructure. In future iterations, we will also support NodeJS.

#### Domain

Once you've created a pipeline using the Reapit IaaS Platform. The Pipeline will be assigned a sub domain on the Reapit cloud url in the format: `https://{sub-domain}.iaas.paas.reapit.cloud.`&#x20;

#### SSL Certificate

The domain supplied with your IaaS hosting will include an SSL Certificate making your application more secure. Enabling the `https` protocol.

#### Real time updates

The Reapit IaaS Platform offers real time updates on your Applications Deployments via the CLI or the Developer Portal.

#### Rollbacks and Version control

The Reapit IaaS Platform enables Reapit customers to control their deployments by redeploying previously deployed versions. Rollbacks and targeted version deployments can be trigger via the CLI. In future versions we will support this in the developer portal too.

#### Deploy from your repository&#x20;

#### Github

Install our Github App and grant the Github App permission to your desired repository and use your repository's commit push actions to handle your deployment triggers for you.

#### Bitbucket

Install our Bitbucket App/Plugin and grant the Bitbucket App/Plugin permission to your desired repository and use your repository's commit push action to handle your deployment triggers for you.

### Terminology

#### Pipeline

Pipelines are configurations used to deploy applications to our infrastructure. A pipeline can be created via the developer portal or via CLI.

#### Deployment

A pipeline Deployment is an individual deployment made using a pipeline. The pipeline holds all the configurations such as repository and hosting location. A Deployment is an individual process made to publish your given application to the configured hosting.

#### Release

A Release is almost synonymous with Deployment however Release can be used to describe the trigger of making a deployment such as Release zip and Release Repository commands found in the CLI.

#### CLI

The Command Line Interface tool will enable Reapit customers to create, build, configure, deploy, rollback and manage deployments to the Reapit IaaS Platform.\
\
The CLI tool can be downloaded by those with permission and installed. Once installed you'll need to obtain an api-key from the Reapit Foundations team for the CLI to be authenticated with the IaaS platform.

###




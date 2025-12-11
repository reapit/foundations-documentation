---
description: Custom domain configuration documentation.
---

# Custom Domain

IaaS (Infrastructure as a Service) is a Reapit internal tool for hosting and deploying single page web apps. The aim of IaaS is to provide engineering teams with a platform allowing apps to be deployed quickly without needing involvement from other teams.

Developers can host their React applications on Reapit infrastructure which negates the need to setup project specific infrastructure.

The guide below assumes you are familiar with the [Vite Starter Template](https://foundations-documentation.reapit.cloud/app-development/vite-template) for React



### Creating and Configuring a Pipeline (App) <a href="#creating-and-configuring-a-pipeline-app" id="creating-and-configuring-a-pipeline-app"></a>

**What is a Pipeline?**

Each application you want to deploy with IaaS has a pipeline. Think of this as a CI/CD runner for your app, that responds to events in GitHub, such as a pull request being merged. These events will trigger a deployment which contains four distinct stages:

1. Download Source - the source code is downloaded from GitHub to the IaaS runner environment.
2. Install - any dependencies are installed. As part of the pipeline configuration you specify which package manager you are using, and the IaaS runner will execute install for that package manager (ie `yarn install` when the package manager is set to Yarn)
3. Build - the project gets built. The IaaS runner will execute whatever build command you specify in the pipeline configuration for the chosen package manager (ie `yarn build`)
4. Deploy - the project gets deployed. The IaaS runner will take the built deployment bundle and host it on a dedicated domain which is a system generated web address. Custom domains can be associated to your IaaS environment so more friendly public URLs are available for us.



> IaaS is currently deployed to the eu-west-2 region. As it uses global Cloudfront, apps developed in other regions can still be deployed using this feature and will be served at the edge for low latency, but your pipeline needs to be configured in the Europe DeveloperPortal

**Pipeline Creation**

A pipeline requires a _Client Side App_ to be created from the [DeveloperPortal](https://developers.reapit.cloud/). A newly created _Client Side App_ will automatically trigger the creation of a pipeline which will have a status of _Pre Provisioned_, meaning that it’s ready for use.

<figure><img src="../../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>

**Configure Pipeline**

Before configuring your pipeline, make sure the Reapit GitHub app is installed the repository or organisation you wish to use IaaS with. For information about how to do this, [click here](https://reapit.atlassian.net/wiki/spaces/FOUN/pages/2807955545/IaaS+Documentation#Installing-the-Reapit-Github-App-to-your-repository)

The Configure tab is used to link your IaaS pipeline to your GitHub repository, and setup the commands which will be executed by the IaaS runner environment.

<figure><img src="../../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

The name of the pipeline will default to that of your app. As this is a system generated name, you may want to change this. It’s useful to ensure you can identify a pipeline from the main IaaS page, accessed from the top navigation menu in the DeveloperPortal

The deployment branch is the name of the branch in your GitHub repository that should invoke the IaaS pipeline runner when anything is pushed to that branch. Typically this will be main or master, but you may also have separate development or feature branches that you wish to deploy. Different environments (ie Development and Production) should use different apps in the DeveloperPortal which would have isolated pipelines with different _Deployment Branch_ configurations.

Next, attach the pipeline to your GitHub repository by clicking the _GitHub Repository_ field. A modal will appear that will allow you to sign into GitHub and select from the list of repositories you have access to. If you have access to repositories across different GitHub accounts - for example where you are a collaborator on an external repository - it will also be listed here.

<figure><img src="../../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

Clicking the _Login with GitHub to continue_ button, you’ll be navigated to GitHub where you’ll be asked to select your the user you wish to authenticate with if you have multiple active sessions in your browser:

<figure><img src="../../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

Once you’re logged in, you’ll be navigated back to the pipeline you were configuring. The repository selection modal will appear again and show you the GitHub accounts available to your logged in user, based on where the Reapit GitHub app is installed:

<figure><img src="../../.gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>

Once you’ve selected an installation, you’ll be able to select a repository attached to that installation.

<figure><img src="../../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>

Next, select the _Package Manager_ that your project uses. Typically this is Yarn or Npm, and it’s recommended you configure the same package manager as you use locally for the project.

The build command defines the command that the IaaS pipeline will execute to build your deployable app bundle.

The build directory defines the directory where the IaaS pipeline will look for deployment assets that have been built as part of the build process.

Don’t forget to hit _Save Config_ after you’ve finished configuring the pipeline.

<figure><img src="../../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>

### Installing the Reapit Github App to your repository <a href="#installing-the-reapit-github-app-to-your-repository" id="installing-the-reapit-github-app-to-your-repository"></a>

**Reapit Internal users can skip this step as the app is installed Globally in our Enterprise tenant - if there are any issues with this, please contact an admin.**

Our [Github app](https://github.com/apps/reapit) is the glue between the IaaS system and GitHub. You can able to install it for all repositories or specific repositories in an account or organisation. On the app page on GitHub, if you have permission to do so, you’ll see a _Configure_ button which will enable you to configure your repositories. Please note that the app is installed globally in the _reapit-global_ enterprise organisation.

<figure><img src="../../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

Once you’ve selected your installation you’ll be prompted with the app settings page where you’ll be able to find the repository access section. Here you’ll be able to configure which repositories the Reapit App has access to.

<figure><img src="../../.gitbook/assets/image (162).png" alt=""><figcaption></figcaption></figure>

> Within Reapit Github Organisations a relevant admin will be required to manage repository access.

### Customising DNS <a href="#customising-dns" id="customising-dns"></a>

When creating new pipelines, a system generated DNS name will be used when deploying your app for the first time. This is typically in the format _foo-bar.iaas.paas.reapit.cloud_. It’s likely you will want to customise this so that more friendly domain names can be used externally.

To setup a custom domain, use the _Custom DNS_ tab which is available on the IaaS Pipeline page for your app in the DeveloperPortal. You can use external domains or the existing _reapit.cloud_ domain. Please note that only employees with the Reapit Connect group membership `FoundationsDeveloperAdmin` can create custom DNS configurations. Administrators can promote users as required in the [DeveloperPortal](https://developers.reapit.cloud/settings/members).

<figure><img src="../../.gitbook/assets/image (163).png" alt=""><figcaption></figcaption></figure>

Clicking _Setup Custom DNS_ will present the setup modal as shown below:

<figure><img src="../../.gitbook/assets/image (164).png" alt=""><figcaption></figcaption></figure>

Enter the custom domain you wish to use for your app and click _Next_. IaaS will start to provision SSL certificates and generate DNS records that need to be added to your DNS database. If you are configuring a `reapit.cloud` domain the creation of CNAME records will be handled for you. This process involves a PR to the DevOps team to setup the DNS records in the right namespace. Once this is done, the _Certificate Status_ will change to _Verified_. Any other domain requires you to setup the records as described onscreen yourself.

<figure><img src="../../.gitbook/assets/image (165).png" alt=""><figcaption></figcaption></figure>

Once the _Certificate Status_ changes to _Verified_. you will be able to reach your deploy app at your chosen domain.

### Demo <a href="#demo" id="demo"></a>

You can watch a demo of IaaS in action below

{% embed url="https://youtu.be/nKeTaD-evzM" %}

### FAQs <a href="#faqs" id="faqs"></a>

* Q: I’ve created a custom domain but need to change it. What should I do?\
  A: You will need to delete your pipeline completely. This process can take a number of minutes, after which you can setup a brand new one as needed
* Q: I’ve created a custom domain using `reapit.cloud` but the Certificate Status still says Unverified after a number of days. What should I do?\
  A: The certificate validation process requires certain DNS records to be present. Until the certificate validation process can access these records, it will not issue the certificate for your chosen domain. When using the `reapit.cloud` domain, the IaaS backend opens a pull request (PR) in the [UK DevOps GitHub repository](https://github.com/reapit-global/uk-devops-infrastructure-core-cdk) to setup the DNS records required by this process. It’s likely that this PR has not yet been merged and changes deployed. Once this happens, the certificate should validate so that your custom domain can be used
* Q: I cannot see the IaaS options in the DeveloperPortal. Why is this?\
  A: As the DeveloperPortal is used by both internal and external developers, access needs to be granted to your developer organisation. Most colleagues will already be part of an organisation that has access, but if not, please [click here ](mailto:appsupport@reapit.com?subject=IaaS%20Access%20Request\&body=Please%20can%20you%20give%20me%20access%20to%20IaaS.%20The%20email%20address%20I%20use%20to%20log%20into%20the%20DeveloperPortal%20is%20%5Byouremail%40reapit.com%5D.%20I%20am%20working%20with%20the%20%5BEnter%20Team%5D)to send an email.
* Q: My deployment keeps failing. Who should I contact?\
  A: When deployments are in progress, logs will become available on the _Deployments_ tab. These can indicate problems with your build process. If you are unable to resolve the problem, please [click here](mailto:appsupport@reapit.com?subject=IaaS%20Deployment%20Problem\&body=I%20am%20having%20an%20issue%20with%20IaaS.%0D%0A%0D%0AThe%20issue%20is%20%5Binsert%20summary%5D%0D%0A%0D%0AApplication%20Details%3A%0D%0AAppId%3A%20%5Bapp%20id%20from%20DeveloperPortal%5D%0D%0APipeline%20Name%3A%20%5BName%20of%20IaaS%20pipeline%5D) to send an email

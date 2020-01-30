# Deployment

We currently deploy static assets to S3 buckets.

* [Develop environment](https://d3ps8i1lmu75tx.cloudfront.net) is triggered by pushs to `develop` branch
* [Production environment](https://dvyjx6qs1jinm.cloudfront.net) is triggered by tag

  pushs with `AS-` prefix, eg. pushing `AS-0.0.1` tag will trigger a build pipeline

  and deploy it's output assets to Production S3 bucket

## Read on:

* [Home](https://github.com/reapit/foundations-documentation/tree/777f5a5c6d6e2d106c049a6fbf696ba3f4ddfd95/Open%20Source/README.md)
* [Getting Started](getting_started.md)
* [Api Platform](api_platform.md)
* [Code Style](code_style.md)
* [Version Control](version_control.md)
* [Definition of Done](definition_of_done.md)


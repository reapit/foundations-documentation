---
description: >-
  A service catalogue of our open source packages, what they do, where they
  deploy, the services they leverage and any additional steps how to work on
  them
---

# Packages

{% hint style="info" %}
Where possible, our applications follow in-house conventions, style guides and design patterns. As such, please read our contributing guide first, along with our Web API section for the majority of usage information. This guide is solely concerned with package-specific information.
{% endhint %}

## Marketplace

The core frontend of the Reapit Foundations platform. Contains all functionality in both the Marketplace and Developer Portal applications.

* **Tech Stack:** React, Redux, React Router, Elements, Cognito Auth, Jest, Cypress, Sass / CSS Modules.
* **Cloud Services:** S3, CloudFront, AWS Cognito, SecretsManager, Sentry
* **Production:** https://marketplace.reapit.cloud
* **Development:** https://dev.marketplace.reapit.cloud ****

## Elements

A UI toolkit for building web applications in the Reapit Marketplace

## Cognito Auth 

A thin wrapper around the AWS SDK and OAuth flow to take the pain out of authenticating your App with Reapit Connect

## React App Scaffolder

## Foundations TS Definitions

Automated TypeScript definitions for the Foundations API Platform

## AML Checklist

An anti-money laundering app, aimed at helping negotiators gather identity checking information from clients and applicants.

## Geo Diary

An app for negotiators on the go. It geo locates the user and assists them with their daily appointments by getting them from A to B.

## Web Components

Embeddable TypeScript widgets to enhance static sites. The library will be built into two different types: as npm package to use with npm project,  as UMD scripts to embed into other static sites.

## Lifetime Legal

Fork of AML App, to extend functionality for Lifetime Legal client.

## GraphQL Server

A GraphQL implementation of the Foundations API. 

## Config Manager

A thin wrapper around AWS Secrets Manager for keeping remote config secure.

Simple wrapper around AWS SDK for managing config objects in AWS Secrets Manager. Exports both CLI and Node versions and is distributed via an NPM Package.

## SMB Small Businesses App

An application to onboard new businesses to the Reapit Agency Cloud CRM.

## Demo Site

A simple HTML app for deploying Reapit Web Components.

## Cognito Custom Mail Lambda

Lambda that intercepts Cognito Emails and applies custom Reapit response




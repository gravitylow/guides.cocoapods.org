---
title: Getting setup with Trunk
order: 3
description: Instructions for creating a CocoaPods user account

---

## What do I need to know about trunk

The CocoaPods trunk is an authentication & CocoaPods API service. In order to submit libraries to CocoaPods you will need to have to be registered and have a session on that device. You can read a little about it's history and development on [the blog](http://blog.cocoapods.org/CocoaPods-Trunk/).

From CocoaPods 0.33 on-wards we have a collection of commands under `pod trunk` to deal with automating the deployment and management of your Podspecs. At any time you can run `pod trunk [command] --help` to see inline help.

### Getting started

Get started by signing up for an account with the command `pod trunk register`, think of this as registering this single device rather than registering a user account. 

We recommend using the full command to give some context when you look at your sessions later, so for example:

```
$ pod trunk register orta@cocoapods.org 'Orta Therox' --description='macbook air'
```

You will then receive an email to the email address verifying the connection between your trunk account and the current computer. You can see you sessions by running `pod trunk me`.

You do not have a password, only a per-computer session token.

### Deploying a library

In the library's folder with the Podspec run `pod trunk push` - note this is different to `pod push` which is used for private pod repos. This will:

 * Lint your Podspec locally
 * After a successful lint pushes the Pod converted to JSON to trunk
 * Trunk will generate the canonical JSON representation of your library

Once the library has been added trunk will submit a web hook to other services alerting it of a new CocoaPod, for example [CocoaDocs.org](http://cocoadocs.org).

### Adding other people as contributors

For libraries with multiple maintainers, the first person to push a version can add other maintainers with the command `pod trunk add-owner` for example to add `kyle@cocoapods.org` to my library `ARAnalytics` I would run:

```
$ pod trunk add-owner ARAnalytics kyle@cocoapods.org
```
 
This will then list all the known library owners.

### Claiming an existing library

If you want to claim a library that someone has already claimed, then you can use [our Claims form](https://trunk.cocoapods.org/claims/new) to say that you are the maintainer / owner of a collection of libraries. Any issues regarding ownership of libraries will be arbitrated by the CocoaPods dev team.

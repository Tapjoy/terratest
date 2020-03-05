---
layout: collection-browser-doc
title: Unit tests, integration tests, end-to-end tests
category: testing-best-practices
excerpt: >-
  See the talk about unit tests, integration tests, end-to-end tests, dependency injection, test parallelism, retries, error handling, and static analysis.
tags: ["testing-best-practices"]
order: 201
nav_title: Documentation
nav_title_link: /docs/
---


For an introduction to Terratest, including unit tests, integration tests, end-to-end tests, dependency injection, test
parallelism, retries, error handling, and static analysis, see the talk "Automated Testing for Terraform, Docker,
Packer, Kubernetes, and More".

<iframe width="100%" height="450" allowfullscreen src="https://www.youtube.com/embed/xhHOW0EF5u8"></iframe>

Link to the video at [infoq.com](https://www.infoq.com/presentations/automated-testing-terraform-docker-packer/).

## Slides

Slides to the video can be found here: [Slides: How to test infrastructure code](https://www.slideshare.net/brikis98/how-to-test-infrastructure-code-automated-testing-for-terraform-kubernetes-docker-packer-and-more){:target="_blank"}.

## Text Summary

### Motivation

One of the biggest issues in the world of devops is fear. Specifically fear of a deployment bringing the world crashing down around you. The best way to avoid that fear, and enable frequent, useful deploys, is testing. Testing is the difference between fear and confidence.

### Static Analysis

Static Analysis looks to test code without deploying it. They fall into roughly three categories. They're easy to use and don't require a lot of setup. They don't catch everything, but they're a good starting point.

#### compilers/parsers/interpreters

These check your syntax and structure, they essentially verify your code "looks" right, and is properly shaped. They make no promises about runtime. Some examples:

![compilers/parsers/interpreters examples](https://image.slidesharecdn.com/automatedtestingforterraformdockerpackerkubernetesandmorev3-191111230112/95/how-to-test-infrastructure-code-automated-testing-for-terraform-kubernetes-docker-packer-and-more-35-638.jpg?cb=1573513421)

This is the most basic type of testing we can do.

#### linters

Linters are good for catching common mistakes. They read through your code and detect things that are wrong, but are not incorrect from a code point of view

![linters examples](https://image.slidesharecdn.com/automatedtestingforterraformdockerpackerkubernetesandmorev3-191111230112/95/how-to-test-infrastructure-code-automated-testing-for-terraform-kubernetes-docker-packer-and-more-38-638.jpg?cb=1573513421)


#### dry run

A form of code execution without deploying. Its sort of the bridge between static analysis and unit testing. It will give some kind of plan output. It won't catch everything but it verifies execution to some extent.

![dry run examples](https://image.slidesharecdn.com/automatedtestingforterraformdockerpackerkubernetesandmorev3-191111230112/95/how-to-test-infrastructure-code-automated-testing-for-terraform-kubernetes-docker-packer-and-more-41-638.jpg?cb=1573513421)

### Unit Tests

Unit testing tests single units of code in isolation

An unit in this case is a single module. If your infrastructure is not divided into a small of small units, then breaking it up into small units is the first step.

Most infrastructure code is about talking to the outside world, which makes isolating the infrastructure code an exercise in futility. The only way to test infrastructure code is to deploy it to a real enviorment! There is no pure unit testing in infrastructure.

Therefore the strategy becomes

1. Deploy your infrastructure
1. Test it works
1. Undeploy your infrastructure

![dry run examples](https://image.slidesharecdn.com/automatedtestingforterraformdockerpackerkubernetesandmorev3-191111230112/95/how-to-test-infrastructure-code-automated-testing-for-terraform-kubernetes-docker-packer-and-more-54-638.jpg?cb=1573513421)

You can find some examples [here](https://github.com/gruntwork-io/infrastructure-as-code-testing-talk)

# Azure Pipelines YAML example



## Build, test, and publish a node package
We have a few syntax improvements coming to add new features and simplify. Theres are rolling out in Q2. The samples below show the before/after in a few different scenarios.

Syntax improvements
* **`use` keyword** - Instead of using Tasks for setting up each language/ecosystem, we've adding a simpler `use` keyword that's similar to Travis' `lang`. It will setup the environment, including authentication to feeds, proxy, version, and more.
* **Automatic test and code coverage reports** - Instead of requiring customers to add Tasks for this, we'll automatically report tests results by parsing the `stdout` for the most popular ecosystem, test runner, and code coverage combinations. This give more automatic value, while enabling customer to customize it if they want it. Test and code coverage reporting insights are two of the features customers get the most excited about.
* **pipeline output caching** - We're adding pipeline output caching so customers can speed up their build times. The main scenario is package caching, but there are other use cases.

Samples - build, test, and publish
* [current syntax](build-test-publish-node-old.yml) 
* [new syntax](build-test-publish-node-new.yml)

Samples - build, test across 3 node versions, and publish
* [current syntax](build-test-publish-node-matrix-old.yml)
* [new syntax](build-test-publish-node-matrix-new.yml)

Samples - build, test across 3 OSes, and publish
* [current syntax](build-test-publish-node-matrix-old.yml)
* [new syntax](build-test-publish-node-matrix-new.yml)

## Build, test, and deploy a node service
These samples off how we're adding native CD concepts to the syntax
* **Stages** - Customers often want to have a set of stages that group multiple deployments and a single owner/approver for that stage. These are often different for each stage and that's required by some regulated industries. Stages let customers group together jobs/deployments and specify a single set of checks/approvals for all the jobs/deployments before they progress to the next stage.
* **Deployments** - By putting this natively in to the syntax, we can provide the lifecycle hooks, but also trace how issues, commits, containers, deployments, and other resource related to one another so customers can diff them and see what is on - and has been on - a specific environment. Often, developers just want to look at the world based on an environemtn instead of the pipeline. This allows us to create experiecnes and associated the data in both directions.
* **Deployment Strategies** - Services are moving to safe deployment by using a number of common stratgies, such as canary, blue/green, and others. We're simplifying adopting this by surfacing a common set of lifecycle events for each strategy independent of the targe resource. As a pipeline author, I don't have to worry about how to setup blue/green on Azure App Service or Kuberenetes. I just specify the action/script I want to run when it's time to change the traffic routing, similar to Spinnaker.

Samples - build, test, and deploy a node service
* [Simple script deployment](build-test-deploy-node-new.yml)
* [Blue/green deployment](build-test-deploy-node-blue-green-new.yml)
* [Blue/green using actions](build-test-deploy-node-blue-green-actions.yml)

# Contribution Guide

## Contributing to Bitrise

_The mobile developer community has made Bitrise what it is today. We're eager to support you as you help us further improve the world's most popular mobile app development platform._ - [bitrise.io](https://go.bitrise.io/community/contributing)

If you wish to contribute to Bitrise, or take part in the community discussions, we have some links for you:

- [Edit existing articles or submit new ones to our docs](https://github.com/bitrise-io/devcenter/).
- [Read our blog](https://blog.bitrise.io/), and [contact us](https://www.bitrise.io/contact) if you whish to write your own blog post.
- [Request a feature, submit an issue, or just talk to other members of our community on our forums.](https://discuss.bitrise.io/)

You can find out more on contributions on [Devcenter.](https://devcenter.bitrise.io/contributors/contributors-index/)

## 🆕 Hacktoberfest 2021

![Hacktoberfest](https://assets-global.website-files.com/5db35de024bb983af1b4e151/614b32cef945bd44510cd3e8_815_hactoberfest%20web%20HERO-p-500.png)

We are super excited that Bitrise is participating in this year's [Hacktoberfest 2021](hacktoberfest.digitalocean.com/) event. This month-long event throughout October gives you the chance to contribute to the Open Source codebase of Bitrise.

Check out [our Hacktoberfest page](https://www.bitrise.io/hacktoberfest-2021) for more details!

### Used credits during Hacktoberfest

Contributors during the Hacktoberfest can ask for plus credits for their Bitrise team if they used up their credits by working on their in the bitrise-steplib Github organization contribution.

### How to ask for plus credits

Open a [support ticket on bitrise](https://support.bitrise.io/hc/en-us/requests) and ask for plus credit during the Hacktoberfest. You'll need to provide your Github user, the pull request you've worked on and your bitrise team's slug.

## Contributing Code to a Bitrise Step

### Fixing bugs

Fixing a simple bug is a great way to start contributing your code to Bitrise. If you found a bug that you would like to fix, please follow this process:

1. Check if there is an existing GitHub issue about the problem, if not, create one.
1. Read the [Coding Guideline](#coding-guideline).
1. Open a Pull Request.

You can also check for open Github issues and [discuss](https://discuss.bitrise.io/) for open bugs that you can contribute to.

### Adding features

🚧 _Currently under construction and will be updated in the future._

We have always been grateful for community contributions that enhance our Steps. Currently we are working on providing a better environment for your features to be added. We will update our Contribution Guide once we are ready to accept your ideas again.

In the meantime, please feel free to share your feature ideas on [Discuss](https://discuss.bitrise.io/c/feature-request).

### Get started

This section helps you get started making changes to an existing Bitrise Step.

Each Step has its own GitHub repository that includes code and the `step.yml` file that defines the configuration of the Step.

Most of the official Bitrise steps are written in [Go](https://golang.org), a simple and efficient programming language. If you are new to the language, we recommend playing with [A Tour of Go](https://tour.golang.org/) and [Go by Example](https://gobyexample.com/).

To get started, let's set up your local environment:

1. [Install Go](https://golang.org/doc/install)
2. [Install Bitrise CLI](https://devcenter.bitrise.io/bitrise-cli/installation/) - or if it's already installed, make sure it's up to date by running `bitrise update` and `bitrise plugin update`
3. Fork and `git clone` the step repo you want to make changes to

#### Anatomy of a Step

A typical Bitrise step folder structure looks like this:

```
├── README.md
├── bitrise.yml       # Workflows for checking code quality and running tests
├── e2e
│   └── bitrise.yml   # Workflows that run end-to-end tests on the step
├── go.mod            # Go module dependencies
├── go.sum            # Dependency checksums
├── main.go           # Main entry point of step, execution starts here
├── main_test.go      # Tests
├── step.yml          # Metadata describing the step (input, outputs, description)
├── vendor/           # Vendored dependencies
```

#### How to test your step

Bitrise is built on Bitrise, so the Steps are tested using CI workflows defined in `bitrise.yml` and `e2e/bitrise.yml`. While making changes to a step, you can run these workflows locally using the Bitrise CLI. 

In the root `bitrise.yml` the `check` workflow lints your code and runs Go tests (e.g. `main_test.go`). End-to-end test workflows are defined in `e2e/bitrise.yml` and you can run a single test workflow by `bitrise run workflow_name --config e2e/bitrise.yml`. These tests run the whole step as part of a larger workflow using a sample mobile project and test the functionality end-to-end.

These test workflows are run automatically on Bitrise when a new PR is opened and the build is approved by the maintainers. This Bitrise project is private at the moment, so you can't see the results if the build failed. Don't worry, once you open a PR, we'll help you fix any failing test.

If you want to test your modified Step in your own real project, you can change the workflow to run your forked version of the step:

```yaml
steps:
- git-clone@6: #replace this
- git::https://github.com/username/steps-git-clone@branchname: # with this 
```


### Coding Guideline

🚧 _Currently under construction and will be updated in the future. The guide is only applicable for Go based Steps. Please follow to conventions of the existing code for Ruby and Bash based Steps._

This section is intended to describe the coding conventions applied for the Step. Please refer to it when contributing code to the repository.

Our single guide currently is to apply [Effective Go](https://golang.org/doc/effective_go.html), which has a great number of tips on writing clear and idiomatic Go.

We also have a [collection of Step-specific guidelines and best practices](https://github.com/bitrise-io/bitrise/blob/master/_docs/step-development-guideline.md).

## Reporting issues

Please refer to our issue template picker if something is not behaving as expected while using the Step. The template picker guides you to the appropriate forum where you can ask your question and we can quickly assist you.

Please note that Github issues not comforming to the bug template will be closed and asked to be reopened.

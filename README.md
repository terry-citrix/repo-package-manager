# Repo Package Manager
The intent is to serve as a sample or template of how to use a public repo as a Package Manager repository.

## What is a Package Manager?
Package Managers offer a lot of benefits when distributing binaries (aka packages), such as automatic checksum validation, determining compatible versions, consistent distribution model, integration with build systems, and installation.

For more info see:
- https://en.wikipedia.org/wiki/Package_manager
- https://cocoapods.org/about
- https://www.geeksforgeeks.org/introduction-apache-maven-build-automation-tool-java-projects/

Examples of package managers include:
- Cocoapods - for Obj-C and Swift libs
- Maven - for Java libs
- NPM - for NodeJS libs
- NuGet - for C# libs
- among others such as Carthage and so on

## What is a Package Manager Repository?
These package managers depend on a Repository (also known as a Registry) to store and distribute the actual packages (the binaries). A repository is really just a directory structure that conforms to a specific way of structuring the packages. Usually package managers have a well-known, or a few well-known, public repositories. Software distributors will sometimes host their own public package manager repositories, and enterpises tend to host their own private repositories.

Examples of well-known package manager repositories include:
- [Cocoapods.org](https://cocoapods.org/) - for Cocoapods
- [Maven Central](https://search.maven.org/) - for Maven packages
- [JBoss](https://central.sonatype.org/) - another Maven repository
- [NPM JS](https://www.npmjs.com/package/repository) - for NodeJS NPM packages

## Why not use an existing Package Manager Repository?
The biggest reason is typically because you wish to distribute an SDK or some other type of library that is not open-source. The development of package managers came about mostly as a result of the open-source community, to easily share and distribute their creations. Sometimes enterprises, even those who contribute to (and create) open-source projects, also need to distribute binaries without the source code for legal or other reasons.

Not all public package manager repositories allow closed-source binaries to be distributed from their repository.

## Why use a Code Repo as a Package Manager Repository?
Public source code repositories, such as github.com and others, offer a convenient way to make available source code and other artifacts. They are increasingly being used for other purposes as well, such as for documentation, meeting notes, wikis, bug tracking, release binaries, and anything else that is tangentially related to code.

As noted, it's not uncommon for source code repositories to also host the binaries, as a convenience to developers.

Turning a source code repository into a package manager repository is therefore just a matter of structuring the directory layout to conform to the package manager's specification.

## Hermes-Messenger
This repo is an example of how to structure a source code repository to also act as package manager repository, either along-side the actual source code or even exclusively just as a package manager repository.

To do so, a sample app is provided that consumes a very simple library called hermes-messenger. This library offers only one function, and all it does is print a message. The hermes-messenger library is written as a library for Obj-C and Java, and published as a Cocoapod package (for Obj-C) and Maven package (for Java).

The sample app then consumes the hermes-messenger package just like it would use any other package from a public package manager repository.

## Structure
This code repo has the following 4 main directories:

- cocoapod
    - Holds the Cocoapod package for hermes-messenger. Used by Obj-C sample app.
- maven
    - Holds the Maven package for hermes-messenger. Used by Java sample app.
- sources/hermes-messenger
    - Holds the source code for the hermes-messenger library.
- sources/sample-app
    - Holds the source code for the sample app which uses the hermes-messenger packge.

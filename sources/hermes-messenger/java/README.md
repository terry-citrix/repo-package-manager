# Hermes Messenger - a sample package

## Compiling
To build and publish the library: At a command-line run `gradlew clean build publish`

## Output
All artifacts (the files built as part of compiling) are located in the `app/build` directory.

## Publishing
The Maven package will be located at `../../../../maven/`, in other words in the `/maven` directory at the root of this repo. These files **are** intended to be submitted to the repo (to origin).

In addition, if you wish to also publish to GitHub's built-in package manager for Maven, then you'll need to:
1. Follow the steps to create a [Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token).
1. Define System Environment variables for `GITHUB_WORK_USERNAME` (with your GitHub username) and `GITHUB_WORK_TOKEN` (with your Personal Access Token).
1. Uncomment the lines in `build.gradle` in the Publishing -> Repositories section.

Note that publishing the same version multiple times to the source code repo is fine, but if you try to publish the same version to GitHub's built-in repo then you'll get a `409 Conflict` error.  It also takes a while (several minutes!) for the repo to show up in GitHub's built-in package manager.

## Running It
The library cannot be run by itself. See the sample-app for how to use it in a working application.

## How to Use It
There are two ways to use this package:
1. From the source code repository. (this works for any public source code repo)
1. From GitHub's built-in package manager for Maven.

### Using the Source Code Repository
To use this Maven package in a Gradle java project, modify your `build.gradle` so that it includes the repo URL as well as adding the dependency:

```groovy
repositories {
    mavenCentral()  // optional
    jcenter()       // optional

    // Add the GitHub repo as a Maven Package Manager Repository.
    maven {
        url "https://raw.githubusercontent.com/terry-citrix/repo-package-manager/main/maven/"
    }
}

dependencies {
    testImplementation 'junit:junit:4.13'       // optional

    // Add a dependency to the hermes-messenger package.
    implementation 'com.terry:hermes-messenger:1.0'
}
```

Then in your source code you can refer to it like any other class.

The package namespace is `com.terry.hermes`, the class name is `Messenger`, and the only available method is `public boolean deliverMessage()`.

For example:
```java
package com.sampleapp;

import com.terry.hermes.Messenger;      // Import the Hermes Messenger class.

public class App {
    public void start() {
        Messenger messenger = new Messenger();      // Instantiate the Messenger class
        messenger.deliverMessage();                 // Invoke the method
    }
}
```

### Using GitHub's Built-In Maven Repository
On the other hand, to use this Maven package stored in GitHub's built-in Maven repository modify your `build.gradle` so that it includes the repo URL as well as adding the dependency:

```groovy
repositories {
    mavenCentral()  // optional
    jcenter()       // optional

    // Add GitHub's built-in repo as a Maven Package Manager Repository.
    maven {
        url "https://maven.pkg.github.com/terry-citrix/repo-package-manager/"
    }
}

dependencies {
    testImplementation 'junit:junit:4.13'       // optional

    // Add a dependency to the hermes-messenger package.
    implementation 'com.terry:hermes-messenger:1.0'
}
```

Then in your source code you can refer to it like any other class.

The package namespace is `com.terry.hermes`, the class name is `Messenger`, and the only available method is `public boolean deliverMessage()`.

For example:
```java
package com.sampleapp;

import com.terry.hermes.Messenger;      // Import the Hermes Messenger class.

public class App {
    public void start() {
        Messenger messenger = new Messenger();      // Instantiate the Messenger class
        messenger.deliverMessage();                 // Invoke the method
    }
}
```


# Hermes Messenger - a sample lib

## Compiling
To build and publish the library: At a command-line run `gradlew clean build publish`

## Output
All artifacts (the files built as part of compiling) are located in the `app/build` directory.

The Maven package on the other hand is located at `../../../../maven/`, in other words in the `/maven` directory at the root of this repo.

## Running It
The library cannot be run by itself. See the sample-app for how to use it in a working application.

## How to Use It
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

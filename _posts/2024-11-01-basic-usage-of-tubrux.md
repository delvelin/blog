---
layout: post
---
## How to Install and Use Tubrux for Analyzing Code Vulnerabilities

##### Table of Contents
- [Minimum Requirements](#minimum-requirements)
- [Installation](#installation)
  - [Installing Tubrux with Maven](#installing-tubrux-with-maven)
  - [Installing Tubrux with Gradle](#installing-tubrux-with-gradle)
- [Using Tubrux in our Java or Kotlin Project](#using-tubrux-in-our-java-or-kotlin-project)
  - [Creating an Instance](#creating-an-instance)
- [Configuring Tubrux](#configuring-tubrux)
- [Running the Analysis](#running-the-analysis)
  - [Example Output](#example-output)
- [Conclusion](#conclusion)

Tubrux is a powerful Java library designed to help developers analyze vulnerabilities in their code, specifically focusing on thread-safety issues and other potential security flaws in Java and Kotlin applications. This article will guide we through the process of installing and using Tubrux in our project.

### Minimum Requirements
- **Java 8** or higher

### Installation

First, please see the <a target="_blank" href="https://tubrux.github.io/blog/2024/10/10/release-histories.html">latest version</a>.

#### Installing Tubrux with Maven

Add the following dependency to our `pom.xml` file:

```xml
<repositories>
    <repository>
        <id>tubrux-repo</id>
        <url>https://repo.repsy.io/mvn/hangga/repo</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>io.tubrux</groupId>
        <artifactId>tubrux</artifactId>
        <version>0.0.2</version>
    </dependency>
</dependencies>
```

After adding the dependency, Maven will automatically download and include Tubrux in our project.

#### Installing Tubrux with Gradle

Add the following to our `build.gradle` file:

```groovy
repositories {
    maven { url 'https://repo.repsy.io/mvn/hangga/repo' }
}

dependencies {
    implementation 'io.tubrux:tubrux:0.0.2'
}
```

Gradle will handle the installation and integrate Tubrux into our project.

### Using Tubrux in our Java or Kotlin Project

#### Creating an Instance

To start using Tubrux, we need to create an instance of the main class where the analysis will be performed.

In **Java**, the following example demonstrates how to create an instance of the main class:

```java
public class Main {
    public static void main(String[] args) {
        new Tubrux()
            .setShowDate(true)
            .setDetectSensitiveData(true)
            .scan();
    }
}
```

In **Kotlin**, the process is similar:

```java
fun main() {
    Tubrux()
        .setShowDate(true)
        .setDetectSensitiveData(true)
        .scan()
}
```

### Configuring Tubrux

Tubrux offers several configuration options to customize the analysis based on our needs. we can configure these options before running the analysis.

The following options are available for configuration:

| **Configuration Option**         | **Description**                                                                                         | **Default Value** |
|-----------------------------------|---------------------------------------------------------------------------------------------------------|-------------------|
| `setShowDate(boolean value)`      | Whether or not to display the date in the output. Set to `false` to disable.                           | `false`            |
| `setDetectDeadlock(boolean value)`| Whether or not to detect deadlocks during analysis. Set to `false` to disable deadlock detection.       | `false`            |
| `setDetectSensitiveData(boolean value)` | Whether or not to detect sensitive data (e.g., passwords, tokens) in the code. Set to `false` to disable. | `false`            |
| `setIgnoreCommentBlock(boolean value)`  | Whether or not to include comment blocks in the analysis. Set to `true` to ignore comment blocks.     | `false`           |


### Running the Analysis

Once we have created an instance of `Tubrux` and set the configurations, we can perform the analysis on our codebase. The analysis will check for vulnerabilities related to thread safety, deadlocks, sensitive data exposure, and more.

#### Example Output

The output from the analysis will show detailed reports about the potential vulnerabilities detected in our code. Here’s an example of what the output might look like:

<img src="https://github.com/tubrux/blog/blob/dark/_posts/example-output.png?raw=true"/>

### Attention, please

It is important to note that this library is very useful for the development stage. But because tubrux works by checking each line of code, it is **not recommended for the production stage**.

### Conclusion

Tubrux is a valuable tool for any Java or Kotlin developer looking to ensure the security and thread-safety of their code. With easy installation via Maven or Gradle, flexible configuration options, and detailed vulnerability analysis reports, Tubrux can help we identify and mitigate potential risks in our codebase effectively.

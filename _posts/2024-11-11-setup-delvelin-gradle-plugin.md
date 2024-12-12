---
title:  "Setup Delvelin Gradle Plugin"
layout: post
---

## Add the plugin to your Gradle project.

### **1. Kotlin DSL**
```kotlin
plugins {
    id("io.github.hangga.delvelin") version "0.1.1-beta"
}
```

### **2. Groovy DSL**
```groovy
plugins {
    id 'io.github.hangga.delvelin' version '0.1.1-beta'
}
```

## **Configuration**

Configure Delvelin using the `delvelin` extension.

```groovy
delvelin {
    outputFileFormat = 'JSON' // Options: LOG, JSON, HTML
    showDate = true
    showSaveDialog = false
}
```

## **Running Delvelin Analyzer**

### 1. On Local Machine

Run the `delvelinScan` task to analyze your project:
```bash
./gradlew delvelinScan
```

If we are using Intellij IDEA, we can also use the gradle menu in the sidebar:

<img width="400" src="https://github.com/hangga/delvelin/blob/main/doc/delvelin-scan-gradle-menu.png?raw=true" alt="sidebar"/>


### 2. On Gitlab CI
Add `delvelinScan` gradle task to our pipeline configuration, for example:
```yaml
stages:
  - test

gradle-scan:
  stage: test
  image: gradle:7.6-jdk8
  script:
    - gradle delvelinScan
  only:
    - main
    - develop
```


## **Configurations**

| **Parameter**    | **Type**  | **Default**       | **Description**                                      |
|------------------|-----------|-------------------|------------------------------------------------------|
| `outputFileFormat`   | `String`  | `LOG`             | `LOG`, `JSON`, `HTML`.               |
| `showDate`       | `Boolean` | `true`            | Show date in the output.                            |
| `showSaveDialog` | `Boolean` | `false`           | Prompt a save dialog after the scan.                |

## Example Output

<a target="_blank" href="https://delvelin.github.io/docs/vulnerability-report.html">HTML Format</a>
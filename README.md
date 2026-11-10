# Maven Pipeline Project

A simple Java Maven application used to demonstrate building a Maven project with a Jenkins Declarative Pipeline.

## Project structure

```text
maven-pipeline-project/
├── pom.xml
├── Jenkinsfile
├── src/
│   ├── main/java/HelloWorld.java
│   └── test/java/HelloWorldTest.java
└── .gitignore
```

## Requirements

- JDK 21 (the Maven compiler targets Java 17)
- Apache Maven 3.9.x
- Jenkins with Pipeline, Git, JUnit and Git client plugins

## Run locally on Windows

From the repository root:

```cmd
mvn clean test package
```

The packaged JAR is created at:

`target/maven-pipeline-project-1.0.jar`

## Jenkins configuration

In **Manage Jenkins → Tools**, configure:

- JDK installation name: `JDK21`
- Maven installation name: `Maven`

Create a Pipeline job and select **Pipeline script from SCM**:

- SCM: Git
- Repository URL: `https://github.com/chalapathi-dotcom/maven-pipeline-project.git`
- Branch: `*/main`
- Script Path: `Jenkinsfile`

Then select **Build Now** and inspect **Console Output**.

The pipeline stages are Checkout, Build, Test and Package. It archives the generated JAR as a Jenkins build artifact.

# Gitlab Shell Client

[![Build Status](https://travis-ci.org/feedhenry/gitlab-shell-client.svg?branch=master)](https://travis-ci.org/feedhenry/gitlab-shell-client) [![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.feedhenry.gitlabshell/gitlab-shell-client/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.feedhenry.gitlabshell/gitlab-shell-client)

Java Client for remote administration of Gitlab Shell

## Installation

### Maven (pom.xml)

```xml
<dependency>
    <groupId>com.feedhenry.gitlabshell</groupId>
    <artifactId>gitlab-shell-client</artifactId>
    <version>X.Y.Z</version>
</dependency>
```

### Gradle (build.gradle)

```groovy
dependencies {
  compile 'com.feedhenry.gitlabshell:gitlab-shell-client:X.Y.Z'
}
```

## Usage

```java
GLSClient client = new GLSClient.Builder()
  .user("git")
  .host("127.0.0.1")
  .port(22)
  .publicKey("ssh-rsa AAAA....")
  .privateKey("-----BEGIN RSA PRIVATE KEY-----\nMIIEow....\n-----END RSA PRIVATE KEY-----")
  .build();

List<GLSKey> keys = client.listKeys();

String[] projects = client.getProjects();

client.addProject("myrepos/repo1");

client.rmProject("myrepos/repo1");

client.addKey("user1", "ssh-rsa AAAA.... user@example.com");

client.rmKey("user1");
```

To run a custom ssh command

```java
client.executeCommand("echo 'hello'");
```

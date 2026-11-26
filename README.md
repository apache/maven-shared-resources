<!---
 Licensed to the Apache Software Foundation (ASF) under one or more
 contributor license agreements.  See the NOTICE file distributed with
 this work for additional information regarding copyright ownership.
 The ASF licenses this file to You under the Apache License, Version 2.0
 (the "License"); you may not use this file except in compliance with
 the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
-->

# Apache Maven Shared Resources

[![Apache License, Version 2.0, January 2004](https://img.shields.io/github/license/apache/maven.svg?label=License)](https://www.apache.org/licenses/LICENSE-2.0)
[![Maven Central](https://img.shields.io/maven-central/v/org.apache.maven.shared/maven-shared-resources.svg?label=Maven%20Central)](https://central.sonatype.com/artifact/org.apache.maven.shared/maven-shared-resources)
[![Reproducible Builds](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/jvm-repo-rebuild/reproducible-central/master/content/org/apache/maven/shared/maven-shared-resources/badge.json)](https://github.com/jvm-repo-rebuild/reproducible-central/blob/master/content/org/apache/maven/shared/maven-shared-resources/README.md)
[![Verify](https://github.com/apache/maven-shared-resources/actions/workflows/maven-verify.yml/badge.svg)](https://github.com/apache/maven-shared-resources/actions/workflows/maven-verify.yml)

The build configuration shared by Apache Maven projects: Checkstyle rules, license
headers, and formatter settings for Spotless and IDEs. The
[Maven parent POM](https://maven.apache.org/pom/maven/) adds this artifact as a
dependency of the Checkstyle and Spotless plugins, which then read each file from the
classpath as `config/<name>`.

- Documentation: <https://maven.apache.org/shared/maven-shared-resources/>
- Issues: <https://github.com/apache/maven-shared-resources/issues>
- Contributing: <https://maven.apache.org/guides/development/guide-maven-development.html>

## What this is

The artifact holds these files under `config/`:

| File | Purpose |
|---|---|
| `maven_checks_nocodestyle.xml` | Checkstyle rules without the layout, import and header checks that Spotless covers; the parent POM uses this one |
| `maven_checks.xml` | Checkstyle rules including layout checks, for builds without Spotless |
| `maven-header.txt` | License header as a regular expression, for the Checkstyle header check |
| `maven-header-plain.txt` | License header as plain text, for the Spotless `licenseHeader` step |
| `maven-eclipse-importorder.txt` | Import order for the Spotless `importOrder` step and Eclipse |
| `maven-eclipse-codestyle.xml` | Eclipse formatter profile matching palantir-java-format |
| `maven-idea-codestyle-2022.xml` | IntelliJ IDEA code style approximating palantir-java-format; the palantir-java-format plugin gives exact output |
| `maven-groovy-eclipse.properties` | Groovy-Eclipse formatter settings for Groovy scripts, such as invoker hook scripts (Spotless `greclipse` step) |

A change here reaches projects only through a parent POM release: release this
repository first, then update `version.maven-shared-resources` in the parent POM.

## Build

```shell
mvn verify
```

# Quick Start

```
mvn --version
mvn -help
mvn -B archetype:generate -DgroupId=com.wearehw3a.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4
mvn clean package
mvn compile
mvn test
mvn package -Pdist '-Dmaven.test.skip=true' -am
mvn dependency:tree
mvn site:site
```

# Links

+ [maven repo](https://mvnrepository.com)


# FAQ

## 1. What are included in build cycle?

- validate
- generate-sources
- process-sources
- generate-resources
- process-resources
- compile

## 2. How many phases are included?

- validate
- compile
- test
- package
- integration-test
- verify
- install
- deploy

## 3. What is the standard directory layout? 

see [directory layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)

All things under the directory `src/main/resources` will be copied to target directory.

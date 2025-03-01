# Migrate to Spring Boot 2.7

**org.openrewrite.java.spring.boot2.UpgradeSpringBoot\_2\_7**
_Upgrade to Spring Boot 2.7_

## Source

[Github](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-boot-27.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite.recipe/rewrite-spring/4.34.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.34.0


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-spring:4.34.0` in your build file or by running a shell command (in which case no build changes are needed): 

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("org.openrewrite.java.spring.boot2.UpgradeSpringBoot_2_7")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:4.34.0")
}
```
{% endcode %}
{% endtab %}

{% tab title="Maven POM" %}
{% code title="pom.xml" %}
```markup
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>4.42.0</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.spring.boot2.UpgradeSpringBoot_2_7</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>4.34.0</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:LATEST \
  -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.UpgradeSpringBoot_2_7
```
{% endcode %}
{% endtab %}
{% endtabs %}


## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Migrate to Spring Boot 2.6](../../../java/spring/boot2/upgradespringboot_2_6.md)
* [Upgrade Maven dependency version](../../../maven/upgradedependencyversion.md)
  * groupId: `org.springframework.boot`
  * artifactId: `*`
  * newVersion: `2.7.x`
  * overrideManagedVersion: `true`
  * retainVersions: `[mysql:mysql-connector-java]`
* [Upgrade Maven parent project version](../../../maven/upgradeparentversion.md)
  * groupId: `org.springframework.boot`
  * artifactId: `spring-boot-starter-parent`
  * newVersion: `2.7.x`
  * retainVersions: `[mysql:mysql-connector-java]`
* [Spring Security 5.4 introduces the ability to configure HttpSecurity by creating a SecurityFilterChain bean](../../../java/spring/boot2/websecurityconfigureradapter.md)
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.boot.web.server.LocalServerPort`
  * newFullyQualifiedTypeName: `org.springframework.boot.test.web.server.LocalServerPort`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.boot.actuate.autoconfigure.web.server.LocalManagementPort`
  * newFullyQualifiedTypeName: `org.springframework.boot.test.web.server.LocalManagementPort`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.boot.rsocket.context.LocalRSocketServerPort`
  * newFullyQualifiedTypeName: `org.springframework.boot.test.rsocket.server.LocalRSocketServerPort`
* [Migrate Spring Boot properties to 2.7](../../../java/spring/boot2/springbootproperties_2_7.md)
* [Change Maven dependency groupId, artifactId and/or the version](../../../maven/changedependencygroupidandartifactid.md)
  * oldGroupId: `mysql`
  * oldArtifactId: `mysql-connector-java`
  * newGroupId: `com.mysql`
  * newArtifactId: `mysql-connector-j`
  * newVersion: `8.0.x`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.UpgradeSpringBoot_2_7
displayName: Migrate to Spring Boot 2.7
description: Upgrade to Spring Boot 2.7
recipeList:
  - org.openrewrite.java.spring.boot2.UpgradeSpringBoot_2_6
  - org.openrewrite.maven.UpgradeDependencyVersion:
      groupId: org.springframework.boot
      artifactId: *
      newVersion: 2.7.x
      overrideManagedVersion: true
      retainVersions: [mysql:mysql-connector-java]
  - org.openrewrite.maven.UpgradeParentVersion:
      groupId: org.springframework.boot
      artifactId: spring-boot-starter-parent
      newVersion: 2.7.x
      retainVersions: [mysql:mysql-connector-java]
  - org.openrewrite.java.spring.boot2.WebSecurityConfigurerAdapter
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.boot.web.server.LocalServerPort
      newFullyQualifiedTypeName: org.springframework.boot.test.web.server.LocalServerPort
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.boot.actuate.autoconfigure.web.server.LocalManagementPort
      newFullyQualifiedTypeName: org.springframework.boot.test.web.server.LocalManagementPort
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.boot.rsocket.context.LocalRSocketServerPort
      newFullyQualifiedTypeName: org.springframework.boot.test.rsocket.server.LocalRSocketServerPort
  - org.openrewrite.java.spring.boot2.SpringBootProperties_2_7
  - org.openrewrite.maven.ChangeDependencyGroupIdAndArtifactId:
      oldGroupId: mysql
      oldArtifactId: mysql-connector-java
      newGroupId: com.mysql
      newArtifactId: mysql-connector-j
      newVersion: 8.0.x

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.spring.boot2.UpgradeSpringBoot_2_7)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

# Use `AtomicReference#weakCompareAndSetPlain(T, T)`

**org.openrewrite.java.migrate.concurrent.MigrateAtomicReferenceWeakCompareAndSetToWeakCompareAndSetPlain**
_Use `AtomicReference#weakCompareAndSetPlain(T, T)` instead of the deprecated `AtomicReference#weakCompareAndSet(T, T)` in Java 9 or higher._

## Source

[Github](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/java-concurrent-apis.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite.recipe/rewrite-migrate-java/1.18.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 1.18.0


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:1.18.0` in your build file or by running a shell command (in which case no build changes are needed): 

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.concurrent.MigrateAtomicReferenceWeakCompareAndSetToWeakCompareAndSetPlain")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:1.18.0")
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
            <recipe>org.openrewrite.java.migrate.concurrent.MigrateAtomicReferenceWeakCompareAndSetToWeakCompareAndSetPlain</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>1.18.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:LATEST \
  -Drewrite.activeRecipes=org.openrewrite.java.migrate.concurrent.MigrateAtomicReferenceWeakCompareAndSetToWeakCompareAndSetPlain
```
{% endcode %}
{% endtab %}
{% endtabs %}


## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Change method name](../../../java/changemethodname.md)
  * methodPattern: `java.util.concurrent.atomic.AtomicReference weakCompareAndSet(..)`
  * newMethodName: `weakCompareAndSetPlain`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.concurrent.MigrateAtomicReferenceWeakCompareAndSetToWeakCompareAndSetPlain
displayName: Use `AtomicReference#weakCompareAndSetPlain(T, T)`
description: Use `AtomicReference#weakCompareAndSetPlain(T, T)` instead of the deprecated `AtomicReference#weakCompareAndSet(T, T)` in Java 9 or higher.
recipeList:
  - org.openrewrite.java.ChangeMethodName:
      methodPattern: java.util.concurrent.atomic.AtomicReference weakCompareAndSet(..)
      newMethodName: weakCompareAndSetPlain

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.migrate.concurrent.MigrateAtomicReferenceWeakCompareAndSetToWeakCompareAndSetPlain)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

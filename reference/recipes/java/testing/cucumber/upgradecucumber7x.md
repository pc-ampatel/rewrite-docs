# Upgrade to Cucumber-JVM 7.x

**org.openrewrite.java.testing.cucumber.UpgradeCucumber7x**
_Upgrade to Cucumber-JVM 7.x from any previous version._

### Tags

* cucumber
* testing

## Source

[Github](https://github.com/openrewrite/rewrite-testing-frameworks/blob/main/src/main/resources/META-INF/rewrite/cucumber.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-testing-frameworks/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite.recipe/rewrite-testing-frameworks/1.35.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-testing-frameworks
* version: 1.35.0


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-testing-frameworks:1.35.0` in your build file or by running a shell command (in which case no build changes are needed): 

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("org.openrewrite.java.testing.cucumber.UpgradeCucumber7x")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-testing-frameworks:1.35.0")
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
            <recipe>org.openrewrite.java.testing.cucumber.UpgradeCucumber7x</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-testing-frameworks</artifactId>
            <version>1.35.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-testing-frameworks:LATEST \
  -Drewrite.activeRecipes=org.openrewrite.java.testing.cucumber.UpgradeCucumber7x
```
{% endcode %}
{% endtab %}
{% endtabs %}


## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Upgrade to Cucumber-JVM 5.x](../../../java/testing/cucumber/upgradecucumber5x.md)
* [Cucumber-Java8 migration to Cucumber-Java](../../../java/testing/cucumber/cucumberjava8tojava.md)
* [Drop SummaryPrinter](../../../java/testing/cucumber/dropsummaryprinter.md)
* [Replace Cucumber-Java step definition regexes with Cucumber expressions](../../../java/testing/cucumber/regextocucumberexpression.md)
* [Cucumber to JUnit Test Suites](../../../java/testing/cucumber/cucumbertojunitplatformsuite.md)
* [Upgrade Maven dependency version](../../../maven/upgradedependencyversion.md)
  * groupId: `io.cucumber`
  * artifactId: `*`
  * newVersion: `7.x`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.testing.cucumber.UpgradeCucumber7x
displayName: Upgrade to Cucumber-JVM 7.x
description: Upgrade to Cucumber-JVM 7.x from any previous version.
tags:
  - cucumber
  - testing
recipeList:
  - org.openrewrite.java.testing.cucumber.UpgradeCucumber5x
  - org.openrewrite.java.testing.cucumber.CucumberJava8ToJava
  - org.openrewrite.java.testing.cucumber.DropSummaryPrinter
  - org.openrewrite.java.testing.cucumber.RegexToCucumberExpression
  - org.openrewrite.java.testing.cucumber.CucumberToJunitPlatformSuite
  - org.openrewrite.maven.UpgradeDependencyVersion:
      groupId: io.cucumber
      artifactId: *
      newVersion: 7.x

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.testing.cucumber.UpgradeCucumber7x)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

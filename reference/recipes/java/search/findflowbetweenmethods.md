# Finds flow between two methods

**org.openrewrite.java.search.FindFlowBetweenMethods**
_Takes two patterns for the start/end methods to find flow between._

## Source

[Github](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/java/org/openrewrite/java/search/FindFlowBetweenMethods.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-java/7.38.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.38.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | startMethodPattern | A [method pattern](/reference/method-patterns.md) that is used to find matching the start point's method invocations. |
| `Boolean` | startMatchOverrides | *Optional*. When enabled, find methods that are overrides of the [method pattern](/reference/method-patterns.md). |
| `String` | endMethodPattern | A [method pattern](/reference/method-patterns.md) that is used to find matching the end point's method invocations. |
| `Boolean` | endMatchOverrides | *Optional*. When enabled, find methods that are overrides of the [method pattern](/reference/method-patterns.md). |
| `String` | target | The part of the method flow should traverse to |
| `String` | flow | When enabled, show the data or taint flow of the method invocation. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.FindFlowBetweenMethodsExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.FindFlowBetweenMethodsExample
displayName: Finds flow between two methods example
recipeList:
  - org.openrewrite.java.search.FindFlowBetweenMethods:
      startMethodPattern: java.util.List add(..)
      startMatchOverrides: null
      endMethodPattern: java.util.List add(..)
      endMatchOverrides: null
      target: null
      flow: null
```
{% endcode %}


Now that `com.yourorg.FindFlowBetweenMethodsExample` has been defined activate it in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("com.yourorg.FindFlowBetweenMethodsExample")
}

repositories {
    mavenCentral()
}

```
{% endcode %}
{% endtab %}

{% tab title="Maven" %}
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
            <recipe>com.yourorg.FindFlowBetweenMethodsExample</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}
{% endtabs %}


## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.search.FindFlowBetweenMethods)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

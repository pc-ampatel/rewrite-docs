# Find YAML properties

**org.openrewrite.yaml.search.FindProperty**
_Find a YAML property. Nested YAML mappings are interpreted as dot separated property names, i.e.  as Spring Boot interprets `application.yml` files._

## Source

[Github](https://github.com/openrewrite/rewrite/blob/main/rewrite-yaml/src/main/java/org/openrewrite/yaml/search/FindProperty.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-yaml/7.38.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-yaml
* version: 7.38.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | propertyKey | The key to look for. Glob is supported. |
| `Boolean` | relaxedBinding | *Optional*. Whether to match the `propertyKey` using [relaxed binding](https://docs.spring.io/spring-boot/docs/2.5.6/reference/html/features.html#features.external-config.typesafe-configuration-properties.relaxed-binding) rules. Default is `true`. Set to `false`  to use exact matching. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.FindPropertyExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.FindPropertyExample
displayName: Find YAML properties example
recipeList:
  - org.openrewrite.yaml.search.FindProperty:
      propertyKey: management.metrics.binders.*.enabled
      relaxedBinding: null
```
{% endcode %}


Now that `com.yourorg.FindPropertyExample` has been defined activate it in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("com.yourorg.FindPropertyExample")
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
            <recipe>com.yourorg.FindPropertyExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.yaml.search.FindProperty)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

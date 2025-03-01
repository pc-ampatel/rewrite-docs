# Change Gradle project Java compatibility

**org.openrewrite.gradle.ChangeJavaCompatibility**
_Find and updates the Java compatibility for the Gradle project._

## Source

[Github](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/java/org/openrewrite/gradle/ChangeJavaCompatibility.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-gradle/7.38.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 7.38.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | newVersion | The Java version to update source compatibility to. All allowed variations of Gradle's `org.gradle.api.JavaVersion` are allowed. This means that we accept versions in the form of doubles (ex. 1.8, 1.11), whole numbers (ex. 8, 11), strings (ex. "1.8", "8", '1.11', '11'), and `org.gradle.api.JavaVersion` enum values (ex. `VERSION_1_8`, `VERSION_11`, `JavaVersion.VERSION_1_8`, `JavaVersion.VERSION_11`). |
| `String` | compatibilityType | The compatibility type to change |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangeJavaCompatibilityExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangeJavaCompatibilityExample
displayName: Change Gradle project Java compatibility example
recipeList:
  - org.openrewrite.gradle.ChangeJavaCompatibility:
      newVersion: 11
      compatibilityType: null
```
{% endcode %}


Now that `com.yourorg.ChangeJavaCompatibilityExample` has been defined activate it in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("com.yourorg.ChangeJavaCompatibilityExample")
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
            <recipe>com.yourorg.ChangeJavaCompatibilityExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.gradle.ChangeJavaCompatibility)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

# Add the Gradle Enterprise plugin

**org.openrewrite.gradle.plugins.AddGradleEnterprise**
_Add the Gradle Enterprise plugin to `settings.gradle(.kts)`._

## Source

[Github](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/java/org/openrewrite/gradle/plugins/AddGradleEnterprise.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-gradle/7.38.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 7.38.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | version | An exact version number or node-style semver selector used to select the version number. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.AddGradleEnterpriseExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.AddGradleEnterpriseExample
displayName: Add the Gradle Enterprise plugin example
recipeList:
  - org.openrewrite.gradle.plugins.AddGradleEnterprise:
      version: 3.x
```
{% endcode %}


Now that `com.yourorg.AddGradleEnterpriseExample` has been defined activate it in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("com.yourorg.AddGradleEnterpriseExample")
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
            <recipe>com.yourorg.AddGradleEnterpriseExample</recipe>
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


## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Add a Gradle settings plugin](../../gradle/plugins/addsettingsplugin.md)
  * pluginId: `com.gradle.enterprise`
  * version: ``
* [Update a Gradle plugin by id](../../gradle/plugins/upgradepluginversion.md)
  * pluginIdPattern: `com.gradle.enterprise`
  * newVersion: ``

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.gradle.plugins.AddGradleEnterprise
displayName: Add the Gradle Enterprise plugin
description: Add the Gradle Enterprise plugin to `settings.gradle(.kts)`.
version: 

recipeList:
  - org.openrewrite.gradle.plugins.AddSettingsPlugin:
      pluginId: com.gradle.enterprise
      version: 
  - org.openrewrite.gradle.plugins.UpgradePluginVersion:
      pluginIdPattern: com.gradle.enterprise
      newVersion: 

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.gradle.plugins.AddGradleEnterprise)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

# Add cron workflow trigger

**org.openrewrite.github.AddCronTrigger**
_The `schedule` [event](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events) allows you to trigger a workflow at a scheduled time._

## Source

[Github](https://github.com/openrewrite/rewrite-github-actions/blob/main/src/main/java/org/openrewrite/github/AddCronTrigger.java), [Issue Tracker](https://github.com/openrewrite/rewrite-github-actions/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite.recipe/rewrite-github-actions/1.18.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-github-actions
* version: 1.18.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | cron | Using the [POSIX cron syntax](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/crontab.html#tag_20_25_07) or the non standard options @hourly @daily @weekly @weekdays @weekends @monthly @yearly. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.AddCronTriggerExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.AddCronTriggerExample
displayName: Add cron workflow trigger example
recipeList:
  - org.openrewrite.github.AddCronTrigger:
      cron: '@daily'
```
{% endcode %}

Now that `com.yourorg.AddCronTriggerExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-github-actions:1.18.0 in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("com.yourorg.AddCronTriggerExample")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-github-actions:1.18.0")
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
            <recipe>com.yourorg.AddCronTriggerExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-github-actions</artifactId>
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
{% endtabs %}


## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Merge YAML snippet](../yaml/mergeyaml.md)
  * key: `$.on`
  * yaml: `schedule:
  - cron: ""`
  * acceptTheirs: `true`
  * fileMatcher: `.github/workflows/*.yml`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.github.AddCronTrigger
displayName: Add cron workflow trigger
description: The `schedule` [event](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events) allows you to trigger a workflow at a scheduled time.
cron: 

recipeList:
  - org.openrewrite.yaml.MergeYaml:
      key: $.on
      yaml: schedule:
  - cron: ""
      acceptTheirs: true
      fileMatcher: .github/workflows/*.yml

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.github.AddCronTrigger)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

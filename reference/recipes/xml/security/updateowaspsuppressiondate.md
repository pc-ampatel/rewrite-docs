# Update OWASP suppression date bounds

**org.openrewrite.xml.security.UpdateOwaspSuppressionDate**
_Updates the expiration date for OWASP suppressions having a matching cve tag. For use with the OWASP `dependency-check` tool. More details: https://jeremylong.github.io/DependencyCheck/general/suppression.html._

## Source

[Github](https://github.com/openrewrite/rewrite/blob/main/rewrite-xml/src/main/java/org/openrewrite/xml/security/UpdateOwaspSuppressionDate.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-xml/7.38.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-xml
* version: 7.38.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `List` | cveList | Update suppressions having any of the specified CVE tags. |
| `String` | untilDate | *Optional*. Optional. The date to add to the suppression. Default will be 30 days from today. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.UpdateOwaspSuppressionDateExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.UpdateOwaspSuppressionDateExample
displayName: Update OWASP suppression date bounds example
recipeList:
  - org.openrewrite.xml.security.UpdateOwaspSuppressionDate:
      cveList: CVE-2022-1234
      untilDate: 2023-01-01
```
{% endcode %}


Now that `com.yourorg.UpdateOwaspSuppressionDateExample` has been defined activate it in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("com.yourorg.UpdateOwaspSuppressionDateExample")
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
            <recipe>com.yourorg.UpdateOwaspSuppressionDateExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.xml.security.UpdateOwaspSuppressionDate)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

# Atomic Boolean, Integer, and Long equality checks compare their values

**org.openrewrite.java.cleanup.AtomicPrimitiveEqualsUsesGet**
_`AtomicBoolean#equals(Object)`, `AtomicInteger#equals(Object)` and `AtomicLong#equals(Object)` are only equal to their instance. This recipe converts `a.equals(b)` to `a.get() == b.get()`._

### Tags

* RSPEC-2204

## Source

[Github](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/java/org/openrewrite/java/cleanup/AtomicPrimitiveEqualsUsesGet.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-java/7.38.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.38.0


## Usage

This recipe has no required configuration parameters and comes from a rewrite core library. It can be activated directly without adding any dependencies.

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("org.openrewrite.java.cleanup.AtomicPrimitiveEqualsUsesGet")
}

repositories {
    mavenCentral()
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
            <recipe>org.openrewrite.java.cleanup.AtomicPrimitiveEqualsUsesGet</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

{% code title="shell" %}
```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.activeRecipes=org.openrewrite.java.cleanup.AtomicPrimitiveEqualsUsesGet
```
{% endcode %}
{% endtab %}
{% endtabs %}


## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.cleanup.AtomicPrimitiveEqualsUsesGet)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

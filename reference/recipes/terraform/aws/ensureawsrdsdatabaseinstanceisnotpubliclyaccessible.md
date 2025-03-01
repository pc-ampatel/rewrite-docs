# Ensure AWS RDS database instance is not publicly accessible

**org.openrewrite.terraform.aws.EnsureAWSRDSDatabaseInstanceIsNotPubliclyAccessible**
_Ensure AWS RDS database instance is not publicly accessible._

### Tags

* terraform
* AWS
* CKV_AWS_17

## Source

[Github](https://github.com/openrewrite/rewrite-terraform/blob/main/src/main/resources/META-INF/rewrite/aws.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-terraform/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite.recipe/rewrite-terraform/1.17.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-terraform
* version: 1.17.0


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-terraform:1.17.0` in your build file or by running a shell command (in which case no build changes are needed): 

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.38.0")
}

rewrite {
    activeRecipe("org.openrewrite.terraform.aws.EnsureAWSRDSDatabaseInstanceIsNotPubliclyAccessible")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-terraform:1.17.0")
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
            <recipe>org.openrewrite.terraform.aws.EnsureAWSRDSDatabaseInstanceIsNotPubliclyAccessible</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-terraform</artifactId>
            <version>1.17.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-terraform:LATEST \
  -Drewrite.activeRecipes=org.openrewrite.terraform.aws.EnsureAWSRDSDatabaseInstanceIsNotPubliclyAccessible
```
{% endcode %}
{% endtab %}
{% endtabs %}


## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Add Terraform configuration](../../terraform/addconfiguration.md)
  * resourceName: `aws_db_instance`
  * content: `publicly_accessible = false`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.terraform.aws.EnsureAWSRDSDatabaseInstanceIsNotPubliclyAccessible
displayName: Ensure AWS RDS database instance is not publicly accessible
description: Ensure AWS RDS database instance is not publicly accessible.
tags:
  - terraform
  - AWS
  - CKV_AWS_17
recipeList:
  - org.openrewrite.terraform.AddConfiguration:
      resourceName: aws_db_instance
      content: publicly_accessible = false

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.terraform.aws.EnsureAWSRDSDatabaseInstanceIsNotPubliclyAccessible)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

# Migrate deprecated `javax.security.jacc` packages to `jakarta.security.jacc`

**org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization**
_Java EE has been rebranded to Jakarta EE, necessitating a package relocation._

### Tags

* authorization
* security
* javax
* jakarta

## Source

[Github](https://github.com/openrewrite/rewrite-migrate-java), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite.recipe/rewrite-migrate-java/1.16.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 1.16.0


## Usage

This recipe has no required configuration options and can be activated directly after taking a dependency on org.openrewrite.recipe:rewrite-migrate-java:1.16.0 in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.34.0")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:1.16.0")
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
        <version>4.39.0</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>1.16.0</version>
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
```shell
mvn org.openrewrite.maven:rewrite-maven-plugin:4.39.0:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:1.16.0 \
  -DactiveRecipes=org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization
```
{% endcode %}
{% endtab %}
{% endtabs %}

Recipes can also be activated directly from the command line by adding the argument `-Drewrite.activeRecipes=org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization`

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Add Maven dependency](../../../maven/adddependency.md)
  * groupId: `jakarta.authorization`
  * artifactId: `jakarta.authorization-api`
  * version: `2.x`
  * onlyIfUsing: `javax.security.jacc..*`
* [Upgrade Maven dependency version](../../../maven/upgradedependencyversion.md)
  * groupId: `jakarta.authorization`
  * artifactId: `jakarta.authorization-api`
  * newVersion: `2.x`
  * retainVersions: `[]`
* [Rename package name](../../../java/changepackage.md)
  * oldPackageName: `javax.security.jacc`
  * newPackageName: `jakarta.security.jacc`
  * recursive: `true`
* [Remove Maven dependency](../../../maven/removedependency.md)
  * groupId: `javax.security.jacc`
  * artifactId: `javax.security.jacc-api`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization
displayName: Migrate deprecated `javax.security.jacc` packages to `jakarta.security.jacc`
description: Java EE has been rebranded to Jakarta EE, necessitating a package relocation.
tags:
  - authorization
  - security
  - javax
  - jakarta
recipeList:
  - org.openrewrite.maven.AddDependency:
      groupId: jakarta.authorization
      artifactId: jakarta.authorization-api
      version: 2.x
      onlyIfUsing: javax.security.jacc..*
  - org.openrewrite.maven.UpgradeDependencyVersion:
      groupId: jakarta.authorization
      artifactId: jakarta.authorization-api
      newVersion: 2.x
      retainVersions: []
  - org.openrewrite.java.ChangePackage:
      oldPackageName: javax.security.jacc
      newPackageName: jakarta.security.jacc
      recursive: true
  - org.openrewrite.maven.RemoveDependency:
      groupId: javax.security.jacc
      artifactId: javax.security.jacc-api

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.migrate.jakarta.JavaxAuthorizationMigrationToJakartaAuthorization)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
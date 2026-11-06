# Paramichha BOM

One version for all Paramichha libraries. Import the BOM, then add the libraries you need
**without versions**: you always get a set that was released and tested together.

## Use

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.paramichha</groupId>
            <artifactId>paramichha-bom</artifactId>
            <version>1.0.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>

<dependencies>
    <dependency>
        <groupId>com.paramichha</groupId>
        <artifactId>testkit</artifactId>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>com.paramichha</groupId>
        <artifactId>datafactory</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

It works next to Spring Boot's parent or BOM: a project can import many BOMs.

## What it manages

| Library | Artifact |
|---|---|
| [paramichha-utils](https://github.com/smmakvana/paramichha-utils) | `com.paramichha:paramichha-utils` |
| [DataFactory](https://github.com/smmakvana/paramichha-datafactory) | `com.paramichha:datafactory` |
| [TestKit](https://github.com/smmakvana/paramichha-testkit) | `com.paramichha:testkit` |
| [datafactory-catalog](https://github.com/smmakvana/datafactory-catalog) | `com.paramichha:datafactory-catalog` (test fixtures) |

Only Paramichha artifacts. Third-party versions (DataFaker, Jakarta Validation, JUnit...) stay
under your project's control.

## Why it is not a child of paramichha-dev

Importing a BOM also imports everything it inherits. `paramichha-dev` is the parent our libraries
are **built** with and manages third-party versions; inheriting it here would push those versions
into your project. This BOM stands alone and carries only what Maven Central needs.

## Release

Released last by `paramichha-dev/scripts/release-all.sh`, which first releases the libraries and
then sets the versions above to the ones it just published.

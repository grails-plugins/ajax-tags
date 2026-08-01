# Grails Ajax Tags Plugin

[![Java CI](https://github.com/grails-plugins/ajax-tags/actions/workflows/gradle.yml/badge.svg)](https://github.com/grails-plugins/ajax-tags/actions/workflows/gradle.yml)
[![Apache 2.0 License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)

GSP tags for simple Ajax tasks — `formRemote`, `remoteLink`, `remoteField`,
`remoteFunction` and `submitToRemote`. These were part of Grails core before Grails 3
and live here now.

The tags emit jQuery by default, but they generate no JavaScript themselves: the
markup is produced by a pluggable provider, so you can target any library by
registering your own.

## Installation

```groovy
repositories {
    maven { url 'https://repo.grails.org/grails/core' }
}

dependencies {
    implementation 'org.grails.plugins:ajax-tags:8.0.0-SNAPSHOT'
    runtimeOnly 'org.webjars.npm:jquery'   // the plugin does not bundle jQuery
}
```

## Usage

```groovy
class BookController {
    def show() {
        [book: Book.get(params.id)]
    }
}
```

```html
<g:remoteLink action="show" id="1" update="bookDetails">Show book</g:remoteLink>

<div id="bookDetails"></div>
```

`update` takes an element id, or a `[success: ..., failure: ...]` map to handle the
two outcomes separately. Callbacks (`onLoading`, `onLoaded`, `onSuccess`,
`onFailure`, `onComplete`) each take a snippet of JavaScript.

See the [reference guide](src/docs/asciidoc/index.adoc) for the full attribute list
for every tag, and for how to register an alternate provider.

## Building

Requires JDK 21.

```sh
./gradlew check      # compile and run the tests
./gradlew docs       # reference guide + Groovydoc into build/docs
./gradlew assemble   # build the plugin jar
```

## Versions

| Branch | Built against |
|---|---|
| `8.0.x` | Grails 8.0.0-M4 |
| `3.0.x` | Grails 7.0.0-SNAPSHOT |
| `2.0.x` | Grails 6.2.1 |
| `1.0.x` | Grails 4.0.11 |

## License

Apache License 2.0.

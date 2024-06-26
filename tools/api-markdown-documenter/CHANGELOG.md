# @fluid-tools/api-markdown-documenter

## 0.14.0

-   Updated the package to emit ESM only.
-   Fixed a bug where [inline tags](https://tsdoc.org/pages/spec/tag_kinds/#inline-tags) (other than `{@link}` and `{@inheritDoc}`, which are handled specially by API-Extractor) were not handled and resulted in errors being logged to the console.
    Such tags are now handled in the following way:
    -   [{@label}](https://tsdoc.org/pages/tags/label/) tags are simply omitted from the output (they are intended as metadata, not documentation content).
    -   Other custom inline tags are emitted as italicized text.
-   Fixed a bug where pre-escaped text contents (including embedded HTML content) would be incorrectly re-escaped.

### ⚠ BREAKING CHANGES

-   The package now outputs ESM only.
    Consumers will have to migrate accordingly.
-   `DocumentationNode` now has a required `isEmpty` property.
    Implementations will need to provide this.

## 0.13.0

-   Fixed a bug where type parameter information was only being generated for `interface` and `class` items.
-   Adds "Constraint" and "Default" columns to type parameter tables when any are present among the type parameters.

### ⚠ BREAKING CHANGES

-   Update the signature of `createTypeParametersSection` to always generate a `SectionNode` when called, such that consumers don't have to handle a potentially undefined return value.
    If the consumer wants to omit the section (for example when the list of type parameters is empty), they can make the call conditional on their end.
-   Removed `createDocumentWriter`, and exported `DocumentWriter` is now an interface rather than a class.
    A `DocumentWriter` may be instantiated via `DocumentWriter.create` (or you can use your own implementation, which was not previously supported).

## 0.12.0

### ⚠ BREAKING CHANGES

Update `typescript` dependency from `4.x` to `5.x`.

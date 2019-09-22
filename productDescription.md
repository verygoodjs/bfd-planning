# BFD: Product Description
A description of the product used for planning the data model of the system and identify the services and user flows necessary for this product.

## Table of Contents
* [Principal Concepts](#principal-concepts)

## Principal Concepts
* A _theme_ does not apply to a _blog_ but to individual blog _posts_ and _pages_.
  * A _blog_ can have a default _theme_ set, but this should be configurable at the _post_ and _page_ level.
* There are multiple types of _assets_ that can be utilized in a _post_ or a _page_.
  * _Media assets_ are managed in a gallery
    * _Image_, _video_, and _audio_ assets can be uploaded and managed within the gallery
  * _Page assets_ are managed in their own gallery
    * _Scripts_: JS files
    * _Styles_: CSS files
    * _Partials_: HTML templates
  * All assets can be referenced from a _post_ or a _page_.
* The _CMS_ is _theme_ aware: it provides input forms based on the inputs a given _theme_ expects.
* Each _CMS_ page also has a theme applied to it.
* The _Blog Management Portal_ can also have a default _theme_ applied to it, which it will default its _pages_ to.
  * It may be possible for the _Blog Management Portal_ to have a setting to apply _themes_ to its own _pages_?
* _Themes_ can:
  * Dictate their own schema, used to inform the CMS which field keys/types it accepts/requires.
  * Be versioned (semver).
  * Be added to a _post_ or a _page_.


# BFD: Product Description
A description of the product used for planning the data model of the system and identify the services and user flows necessary for this product.

In this document I will provide early ideas and details to describe my vision of this system, its features, and capabilities. This is by no means a proposal of what the early versions of this system must be delivered with.

We can update this document as we develop the system or we can draft up new descriptions and version them. In laying out these ideas I hope to provide a starting point for ideating on the sort of system I would like to see come to life.

## Table of Contents
* [Principal Concepts](#principal-concepts)
* [System](#system)
  * [Actors](#actors)
    * [User](#user)
  * [Blog](#blog)

## Principal Concepts
* A _theme_ does not apply to a _[blog](#blog)_ but to individual blog _posts_ and _pages_.
  * A _[blog](#blog)_ can have a default _theme_ set, but this should be configurable at the _post_ and _page_ level.
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

## System
Description of the components of the entire blog system.

### Actors
The _actors_ are the entities that will interact with this blog system. In this chapter we will describe them. Today there is only one type of _actor_: the _[user](#user)_. In the future perhaps _commenters_ or _subscribers_ may be added to this system.

#### User
A _user_ is an _[actor](#actors)_ who has created an account in the system.

A _user_ has:
* An email address
* A password
* A public id
* A user name
* A display name

A _user_ can perform, among others, the following actions:
* Create _[blogs](#blog)_
* Be given access to a _[blog](#blog)_
* Given the necessary _roles_:
  * Publish _pages_ and _posts_ to a _[blog](#blog)_
  * Create a _draft_ of a _page_ or _post_ for a _[blog](#blog)_
  * Edit _pages_, _posts_, and _drafts_ to a _[blog](#blog)_
  * Configure a _[blog](#blog)_
  * Submit a _post_ or _page_ for publication
  * Approve a pending _post_ or _page_
  * Request changes to a _post_ or _page_
  * Publish updates to _pages_ and _posts_

### Blog
A _blog_ is created by a _[user](#user)_.

A _blog_ has (or can have):
* A title (editable)
* An ID (editable)
* A creator (a _[user](#user)_)
  * This is immutable upon creation
* One or more _[users](#user)_
  * _[Users](#user)_ added to the _blog_ have _roles_
* A public site
* A _management portal_
* _Pages_
* _Posts_
* _Tags_ which can be applied to _pages_ and _posts_
* Base _themes_ (one for _pages_ and one for _posts_)
  * Base _themes_ are configurable with the appropriate roles
  * These are the _themes_ applied by default when creating a _page_ or _post_
* Future ideas?
  * Feeds (RSS, etc)
  * Plugins

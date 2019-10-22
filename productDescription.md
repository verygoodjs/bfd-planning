# BFD: Product Description
A description of the product used for planning the data model of the system and identify the services and user flows necessary for this product.

In this document I will provide early ideas and details to describe my vision of this system, its features, and capabilities. This is by no means a proposal of what the early versions of this system must be delivered with.

We can update this document as we develop the system or we can draft up new descriptions and version them. In laying out these ideas I hope to provide a starting point for ideating on the sort of system I would like to see come to life.

## Table of Contents
* [Principal Concepts](#principal-concepts)
* [System](#system)
  * [Actor](#actor)
    * [User](#user)
  * [Blog](#blog)
    * [Page](#page)
    * [Post](#post)
    * [Theme](#theme)
    * [Tag](#tag)
  * [Role](#role)
    * [Owner](#owner)
    * [Administrator](#administrator)
    * [Developer](#developer)
    * [Editor](#editor)
    * [Contributor](#contributor)

## Principal Concepts
* A _[theme](#theme)_ does not apply to a _[blog](#blog)_ but to individual _[blog](#blog)_ _[posts](#post)_ and _[pages](#page)_.
  * A _[blog](#blog)_ can have a default _[theme](#theme)_ set, but this should be configurable at the _[post](#post)_ and _[page](#page)_ level.
* There are multiple types of _assets_ that can be utilized in a _[post](#post)_ or a _[page](#page)_.
  * _Media assets_ are managed in a gallery
    * _Image_, _video_, and _audio_ assets can be uploaded and managed within the gallery
  * _Page assets_ are managed in their own gallery
    * _Scripts_: JS files
    * _Styles_: CSS files
    * _Partials_: HTML templates
  * All assets can be referenced from a _[post](#post)_ or a _[page](#page)_.
* The _CMS_ is _[theme](#theme)_ aware: it provides input forms based on the inputs a given _[theme](#theme)_ expects.
* Each _CMS_ page also has a theme applied to it.
* The _Blog Management Portal_ can also have a default _[theme](#theme)_ applied to it, which it will default its _[pages](#page)_ to.
  * It may be possible for the _Blog Management Portal_ to have a setting to apply _[themes](#theme)_ to its own _[pages](#page)_?
* _Themes_ can:
  * Dictate their own schema, used to inform the CMS which field keys/types it accepts/requires.
  * Be versioned (semver).
  * Be added to a _[post](#post)_ or a _[page](#page)_.

## System
Description of the components of the entire _[blog](#blog)_ system.

### Actor
The _actors_ are the entities that will interact with this _[blog](#blog)_ system. In this chapter we will describe them. Today there is only one type of _actor_: the _[user](#user)_. In the future perhaps _commenters_ or _subscribers_ may be added to this system.

#### User
A _user_ is an _[actor](#actor)_ who has created an account in the system.

A _user_ has:
* An email address
* A password
* A public id
* A user name
* A display name

A _user_ can perform, among others, the following actions:
* Create _[blogs](#blog)_
* Be given access to a _[blog](#blog)_
* Given the necessary _[roles](#role)_:
  * Publish _[pages](#page)_ and _[posts](#post)_ to a _[blog](#blog)_
  * Create a _[draft](#draft)_ of a _[page](#page)_ or _[post](#post)_ for a _[blog](#blog)_
  * Edit _[pages](#page)_, _[posts](#post)_, and _[drafts](#draft)_ to a _[blog](#blog)_
  * Configure a _[blog](#blog)_
  * Submit a _[post](#post)_ or _[page](#page)_ for publication
  * Approve a pending _[post](#post)_ or _[page](#page)_
  * Request changes to a _[post](#post)_ or _[page](#page)_
  * Publish updates to _[pages](#page)_ and _[posts](#post)_

### Blog
A _blog_ is created by a _[user](#user)_.

A _blog_ has (or can have):
* A title (editable)
* An ID (editable)
* A creator (a _[user](#user)_)
  * This is immutable upon creation
* One or more _[users](#user)_
  * _[Users](#user)_ added to the _blog_ have _[roles](#role)_
* A public site
* A _management portal_
* _[Tags](#tag)_
* _[Pages](#page)_
* _[Posts](#post)_
* _Tags_ which can be applied to _[pages](#page)_ and _[posts](#post)_
* Base _[themes](#theme)_ (one for _[pages](#page)_ and one for _[posts](#post)_)
  * Base _[themes](#theme)_ are configurable with the appropriate _[roles](#role)_
  * These are the _[themes](#theme)_ applied by default when creating a _[page](#page)_ or _[post](#post)_
* Future ideas?
  * Feeds (RSS, etc)
  * Plugins

#### Page
A _page_ is hosted at a configured url endpoint on the _[blog](#blog)_ domain. The content of a _page_ is managed through the _management portal_.

A _page_ can be in one of two states:
* Published
* Unpublished

A _page_ has:
* An author (a _[user](#user)_)
* A date published
* Dates edited
* A version history
* 0 or more _[tags](#tag)_

#### Post
A _post_ is hosted at a dynamically generated and programatically managed URL, sequentially ordered by date it was first publicly published. All _posts_ should live under the same URL path or subdomain. All _posts_ are programatically linked to each other, much like a linked list, with a previous and next _post_.

A _post_ can be in one of two states:
* Published
* Unpublished

A _post_ has:
* An author (a _[user](#user)_)
* A date published
* Dates edited
* A version history
* 0 or more _[tags](#tag)_

#### Draft
A _draft_ is a _[post](#post)_ or _[page](#page)_, or a new version of either, that is awaiting publishing.

_Drafts_ can:
* Be submitted for publishing
* Have requested changes applied to it
* Be versioned with every change submitted
* Be versioned every time it is published

#### Theme
A _theme_ is a layout and set of manageable content for a _[page](#page)_ or a _[post](#post)_.

A _theme_ is attached to a bundle of markup/styles/scripts that are responsible for rendering the _[page](#page)_ or _[post](#post)_.

A _theme_ can be imported from a external repository or managed internally to the _[blog](#blog)_.

A _theme_:
* Dictates a schema of dynamic content it needs to render the _[page](#page)_ or _[post](#post)_
  * This schema dictates the name of the fields as well as the type of data each field accepts
  * The types of fields that may be accepted needs to be ironed out

#### Tag
Each _tag_ is a unique string tracked in the _[blog](#blog)_. _Tags_ can be applied to _[pages](#page)_ and _[posts](#post)_ for categorization purposes. A _[user](#user)_ should be able to access _[pages](#page)_ and _[posts](#post)_ by _tag_.

_Tags_ have:
* A title (string)
* A color (hex code)

_Tags_ can be:
* Created
* Edited: title or color
* Deleted


### Role
_[Users](#user)_ can be assigned _roles_ within a _[blog](#blog)_. Each _role_ comes with different degrees of privileges.

#### Owner
A _[blog](#blog)_ can have one or more _owners_. _Owners_ have all privileges available from all _[roles](#role)_ in addition to _owner_-specific privileges.

Owner-specific privileges:
* Rename the _[blog](#blog)_
* Add, remove _[owner roles](#role)_ 

#### Administrator
An _administrator_ has privileges to manage the _[blog](#blog)_. An _administrator_ has all privileges available from all _[roles](#role)_ in addition to _administrator_-specific privileges except _[owner](#owner)_ privileges.

Administrator-specific privileges:
* Manage _[users](#users)_ on the _[blog](#blog)_
  * Add, remove _[user roles](#role)_ (except for _[owners](#owner)_)

#### Developer
A _developer_ has privileges to manage _plugins_, _[themes](#theme)_, and configurations for a _[blog](#blog)_. A developer has all privileges available from all _[roles](#roles)_ in addition to _developer_-specific privileges with the exception of _[owner](#owner)_ and _[administrator](#administrator)_ privileges.

Developer-specific privileges:
* Manage _plugins_, _[themes](#theme)_, and _tags_
  * Install
  * Edit
  * Remove
* Manage _[blog](#blog)_ configurations
  * Domain configuration?

#### Editor
An _editor_ has privileges to manage _[posts](#post)_ and _[pages](#page)_. They have the rights to publish content.

Editor-specific privileges:
* Manage _[posts](#post)_ and _[pages](#page)_
  * Create a _[draft](#draft)_
  * Submit a _[draft](#draft)_
  * Request changes
  * Edit
  * Publish
  * Unpublish
  * Delete

#### Contributor
A _contributor_ has privileges to create and submit _[posts](#post)_ and _[pages](#page)_.

Contributor-specific privileges:
* Limited management of _[posts](#post)_ and _[pages](#page)_
  * Create a _[draft](#draft)_
  * Submit a _[draft](#draft)_
  * Request changes
  * Edit a _[draft](#draft)_

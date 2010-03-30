# TagBox API draft

## Disclaimer

> **This file is only a draft. Nothing here works for now. This just a document to describe possible future features, the new expected syntax and defaults. Fell free to comment, but for current tagbox stable version, look at the master branch.**

## $().tagbox(*tagboxOptions*);

Creates a TagBox with given `tagboxOptions`.

### `tagboxOptions`

#### `separator`
* Types: RegExp
* Default: `/[,]/`
* Use: Regular expression for splitting tags. Used when user is typing and when loading a previously populated tagbox.

#### `grouping`
* Types: String, one character long
* Default: `'"'`
* Use: Provide the user with a way to create tags containing the separator.

#### `box`
* Type: Selector String
* Default: `'div.tagboxContainer'`
* Use: Tag and class of the box that wraps all tags. If the element you choose is not of this tag, it will be transformed (e.g. $('input.tagbox').tagbox({box:'div.tagbox'}) will transform the inputs into divs).

#### `tag`
* Types: String
* Default: `'tagboxTag'`
* Use: Class name to be used on all tags. The class will be used on the <span> that wraps each tag. If you change that, you'll need to fix the default CSS also.

#### `suggestions`
* Type: Boolean false or selector
* Default: `false`
* Use: This enable elements matching this selector to toggle the a know tag from the tagbox.

#### `fx`
* Type: Boolean
* Default: `true`
* Use: Turn on (`true`) and off (`false`) animations.

## $().tagbox().autocomplete(*autocompleteOptions*);

Acts on a given tagbox (or tagboxes) to enable autocomplete as described by `autocompleteOptions`.

Ideally the autocomplete method should be developed in a separate file. This will make tagbox itself much smaller and enable developers wanting to use the jQuery UI Autocomplete (or any other plugin for that matter) to do so.

### `autocompleteOptions`

#### `method`
* Type: Boolean false, String (selection|list), Function
* Default: `false`
* Use: Choose between different methods to autocomplete as the user types.

#### `dictionary`
* Type: String, Array or Object
* Default: false
* Use: Provides the list of existing tags to use in the autocomplete action.
	* String: The string must contain a list of tags, separated and grouped by the `separator` and `grouping` used in $().tagbox()
	* Array: An array of Strings to be used as suggestions.
	* Object: If you provide an Object, you must also provide a `dictionaryMap` (see bellow).

#### `dictionaryMap`
* Type: Boolean false or Function
* Default: `false`
* Use: Function that translates your autocomplete dictionary object to a string.

#### `listhtml`
* Type: Boolean false or Function
* Default: `false`
* Use: A function that receives an array of matching tags and returns the HTML to be used. Each enabled item must have the class `item`.




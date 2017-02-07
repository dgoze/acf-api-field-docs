# ACF Unofficial API Field Documentation

This documentation will cover the ACF fields which are shipped with ACF and ACF Pro. Since the official documentation is missing field definitions for PHP I wanted to add them for other developers using ACF without the Wordpress UI.

All fields and the definitions where read-out hand by hand from the [ACF Pro Repository](https://github.com/wp-premium/advanced-custom-fields-pro/)

## Table of Contents

* **[Required Field Values](#required-field-values)**
* **[General Field Values](#general-field-values)**
* **[Conditional Logic](#conditional-logic)**
* **Fields**
	* **General Fields**
      * [General Options](#general-options)
      * [Text](#text)
      * [Textarea](#textarea)
      * [Number](#number)
      * [E-Mail](#e-mail)
      * [URL](#url)
      * [Password](#password)
      * [WYSIWYG](#wysiwyg)
      * [Checkbox](#checkbox)
      * [Radio](#radio)
      * [True False](#true-false)
      * [Select](#select)
    * **File Upload Fields**
      * [Image](#image)
      * [File](#file)
	* **Wordpress Related Fields**
      * [Page Link](#page-link)
      * [Taxonomy](#taxonomy)
      * [User](#user)
      * [Relationship](#relationship)
      * [Post Object](#post-object)
    * **Data Fields**
      * [Color Picker](#color-picker)
      * [Date Picker](#date-picker)
      * [Date Time Picker](#date-time-picker)
      * [Google Map](#google-map)
      * [Oembed](#oembed)
      * [Time Picker](#time-picker)
	* **Structure Fields**
      * [Message](#message)
      * [Output](#output)
      * [Tab](#tab)
    * **[Contribution](#contribution)**

---

## Required Field Values

The following values are required by **all fields**.

| name  | options    | description                                          |
| ----- | ---------- | ---------------------------------------------------- |
| label | `<string>` | The text the user will see in the backend            |
| name  | `<string>` | The internal name for acf `get_field()` requests     |
| key   | `<string>` | The internal key of the acf. **Has to be unique**    |
| type  | `<string>` | The type of the field, for example `text` or `image` |

---

## General Field Values

The following values can be used on every field but are **not required**.

| name              | options     | description                                                               |
| ----------------- | ----------- | ------------------------------------------------------------------------- |
| required          | `<boolean>` | Set the field to required                                                 |
| instructions      | `<string>`  | Instructions which are above the field which can be used for instructions |
| wrapper           | `<array>`   | An array containing `width`, `class` and `id` for custom styling          |
| default_value     | `*`         | Value which is going to be set if nothing is filled out                   |
| conditional_logic | `<array>`   | Conditional Logic Setup Array, [Instructions here](#conditional-logic)    |

---

## Conditional Logic

You can hide fields depending on other fields. For this you need conditional arrays. The conditional array is using keys and operators to check if a field is set or not.

```php
<?php

[
	'label' => 'My Field',
	'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'true_false',
    'conditional_logic' => array(
    	array(
        	'field' => 'my_field',
            'operator' => '=='
            'value' => 1
        )
    )
]

?>
```

---



## Text

A simple textfield without any special features.

| name          | options    | description                                |
| ------------- | ---------- | ------------------------------------------ |
| default_value | `<string>` | Default value for this field               |
| maxlength     | `<int>`    | Max length for this field                  |
| placeholder   | `<string>` | Sets the Placeholder of this field         |
| prepend       | `<string>` | Prepends a label in front of the textfield |
| append        | `<string>` | Appends a label in front of the textfield  |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'text',
    'default_value' => '',
    'maxlength' => 0,
    'placeholder' => '',
    'prepend' => '',
    'append' => ''
  ]
?>
```



---



## Textarea

A textarea with multiple lines supporting \<br\> or \<p\> tags.

| name          | options             | description                              |
| ------------- | ------------------- | ---------------------------------------- |
| default_value | `<string>`          | Default value for this field             |
| maxlength     | `<int>`             | Max length for this field                |
| placeholder   | `<string>`          | Sets the Placeholder of this field       |
| new_lines     | `wpautop|br|<none>` | Defines what happens with breaks         |
| rows          | `<int>`             | Defines how many rows are visible without scrolling |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'number',
    'default_value' => '',
    'maxlength' => 0,
    'placeholder' => '',
    'new_lines' => '',
    'rows' => 4
  ]
?>
```



---



## Number

A simple HTML5 number field.

| name          | options    | description                                |
| :------------ | ---------- | ------------------------------------------ |
| default_value | `<string>` | Default value for this field               |
| placeholder   | `<string>` | Sets the Placeholder of this field         |
| min           | `<int>`    | Minimum number allowed                     |
| max           | `<int>`    | Maximum number allowed                     |
| step          | `<int>`    | Incrementation per Step                    |
| prepend       | `<string>` | Prepends a label in front of the textfield |
| append        | `<string>` | Appends a label in front of the textfield  |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'textarea',
    'default_value' => '',
  	'placeholder' => '',
    'min' => 0,
  	'max' => 0,
    'prepend' => '',
	'append' => ''
  ]
?>
```



---



## E-Mail

A simple HTML5 email field.

| name          | options    | description                              |
| :------------ | ---------- | ---------------------------------------- |
| default_value | `<string>` | Default value for this field             |
| placeholder   | `<string>` | Sets the Placeholder of this field       |
| prepend       | `<string>` | Prepends a label in front of the textfield |
| append        | `<string>` | Appends a label in front of the textfield |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'email',
    'default_value' => '',
  	'placeholder' => '',
    'prepend' => '',
	'append' => ''
  ]
?>
```



---



## URL

A url field requiring a valid URL.

| name          | options    | description                        |
| :------------ | ---------- | ---------------------------------- |
| default_value | `<string>` | Default value for this field       |
| placeholder   | `<string>` | Sets the Placeholder of this field |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'url',
    'default_value' => '',
  	'placeholder' => ''
  ]
?>
```



------



## Password

A url field requiring a valid URL.

| name        | options     | description                              |
| :---------- | ----------- | ---------------------------------------- |
| placeholder | `<string>`  | Sets the Placeholder of this field       |
| prepend     | `<string>`  | Prepends a label in front of the textfield |
| append      | `<string>`  | Appends a label in front of the textfield |
| readonly    | `<boolean>` | Toggles the Readonly State of this field |
| disabled    | `<boolean>` | Toggles the disabled State of this field |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'password',
  	'placeholder' => '',
  	'readonly' => 0,
  	'disabled' => 0
  ]
?>
```



---



## WYSIWYG

A Wordpress WYSIWYG field.

| name          | options           | description                              |
| :------------ | ----------------- | ---------------------------------------- |
| default_value | `<string>`        | Default value for this field             |
| tabs          | `all|visual|text` | Defines what kind of tabs are visible    |
| toolbar       | `full|basic`      | Defines what kind of toolbar is going to be |
| media_upload  | `<boolean>`       | Toggles the Media Upload Butt            |
| delay         | `<boolean>`       | Disables the editor until it's activated by the user |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'wysiwyg',
    'default_value' => '',
  	'tabs' => 'all',
  	'toolbar' => 'full',
  	'media_upload' => 1,
  	'delay' => 0
  ]
?>
```



---



## Checkbox

A checkbox field.

| name          | options               | description                              |
| :------------ | --------------------- | ---------------------------------------- |
| default_value | `<string>`            | Default value for this field             |
| layout        | `vertical|horizontal` | Defines the layout                       |
| toggle        | `<boolean>`           | Shows a checkbox to toggle all           |
| return_format | `value|label|array`   | Defines what kind of data is returned    |
| save_custom   | `<boolean>`           | Can custom values be saved to the field  |
| allow_custom  | `<boolean>`           | Allow custom values to be added to the field |
| choices       | `<array>`             | A array containing strings as choices    |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'checkbox',
    'default_value' => '',
  	'layout' => 'horizontal',
  	'toggle' => 1,
  	'return_format' => 'value',
  	'save_custom' => 1,
  	'allow_custom' => 1,
  	'choices' => [
      'choice-1' => 'Choice 1',
      'choice-2' => 'Choice 2'
  	]
  ]
?>
```



---



## Radio

A basic radio field.

| name              | options               | description                           |
| :---------------- | --------------------- | ------------------------------------- |
| default_value     | `<string>`            | Default value for this field          |
| layout            | `vertical|horizontal` | Defines the layout                    |
| other_choice      | `<boolean>`           | Allow other choices                   |
| save_other_choice | `<boolean>`           | Save other choices                    |
| allow_null        | `<boolean>`           | Allow empty inputs                    |
| return_format     | `value|label|array`   | The format of the returned data       |
| choices           | `<array>`             | A array containing strings as choices |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'radio',
    'default_value' => '',
  	'layout' => 'horizontal',
  	'other_choice' => 1,
  	'save_other_choice' => 1,
  	'allow_null' => 0,
  	'return_format' => 'array',
  	'choices' => array(
   		'choice-1' => 'Choice 1',
   		'choice-2' => 'Choice 2'
    )
  ]
?>
```



---



## True False

A true/false checkbox field.

| name          | options      | description                         |
| :------------ | ------------ | ----------------------------------- |
| default_value | `<interger>` | Default value for this field        |
| message       | `<string>`   | A message above the content         |
| ui            | `<boolean>`  | Use a ACF UI Checkbox               |
| ui_on_text    | `<string>`   | Show a text on the UI button        |
| ui_off_text   | `<string>`   | Show the text offside the UI button |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'true_false',
    'default_value' => 0,
    'message' => 'My Message',
    'ui' => 1,
    'ui_on_text' => '',
    'ui_off_text' => ''
  ]
?>
```



---



## Select

A select dropdown field field.

| name          | options      | description                         |
| :------------ | ------------ | ----------------------------------- |
| default_value | `<interger>` | Default value for this field        |
| allow_null | `<boolean>`   | Allow empty inputs         |
| ui            | `<boolean>`  | Use the ACF UI               |
| ajax    | `<boolean>`   | Use AJAX to load the select content        |
| return_format   | `value|label|array`   | Show the text offside the UI button |
| multiple   | `<boolean>`   | Allow more than one input |
| choices   | `<array>` | Array containing the choices |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'select',
	'allow_null' => 0,
    'ajax' => 0,
    'return_format' => 'array',
    'choices' => array(
    	'choice-1' => 'Choice 1',
        'choice-2' => 'Choice 2'
    )
  ]
?>
```



---



## Image

A image upload field.

| name          | options          | description                              |
| :------------ | :--------------- | ---------------------------------------- |
| return_format | `array|url`      | Defines what kind of value is return     |
| preview_size  | `<string>`       | The WP image size which should be shown as a the thumbnail |
| library       | `all|uploadedTo` | Defines if whole media library is accessible or only for this field |
| min_width     | `<int>`          | Defines the min width in px              |
| min_height    | `<int>`          | Defines the min height in px             |
| min_size      | `<int>`          | The minimum size for uploaded images in MB |
| max_width     | `<int>`          | Defines the max width in px              |
| max_height    | `<int>`          | Defines the max height in px             |
| max_size      | `<int>`          | The maximum size for uploaded images     |
| mime_types    | `<string>`       | Allow mime_types to be uploaded          |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'image',
  	'return_format' => 'array',
  	'preview_size' => 'thumbnail',
  	'library' => 'uploadedTo',
  	'min_width' => 100,
  	'min_height' => 50,
  	'min_size' => 0,
  	'max_width' => 800,
  	'max_height' => 600,
  	'max_size' => 1.5,
  	'mime_types' => 'jpg,svg'
  ]
?>
```



---



## File

A file field for file uploads.

| name          | options          | description                              |
| :------------ | ---------------- | ---------------------------------------- |
| return_format | `array|url|id`   | Return format of this field              |
| library       | `all|uploadedTo` | Defines if whole media library is accessible or only for this field |
| min_size      | `<int>`          | Defines the min size of the file in MB   |
| max_size      | `<int>`          | Defines the max size of the file in MB   |
| mime_types    | `<string>`       | Allow mime_types to be uploaded          |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'file',
  	'return_format' => 'array',
  	'library' => 'all|uploadedTo',
  	'min_size' => 0,
  	'max_size' => 5,
  	'mime_types' => 'pdf,zip'
  ]
?>
```


---



## Page Link

Allows you to link a page to this field.

| name           | options     | description                                |
| :------------- | ----------- | ------------------------------------------ |
| post_type      | `<array>`   | An Array containing the allowed post types |
| taxonomy       | `<array>`   | An Array containing the allowed taxonomies |
| allow_null     | `<boolean>` | Allow null as a value                      |
| multiple       | `<boolean>` | Allow more than one input                  |
| allow_archives | `<boolean>` | Allow pages from the archives              |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'page_link',
	'post_type' => array('post', 'page'),
    'taxonomy' => array(),
    'allow_null' => 0,
    'multiple' => 1,
    'allow_archives' => 1
  ]
?>
```



---



## Taxonomy

Allows you to link a taxonomy to this field.

| name           | options     | description                                |
| :------------- | ----------- | ------------------------------------------ |
| taxonomy       | `<string>`  | A taxonomy to be selected for this field 	|
| field_type     | `checkbox|select|radio` | Fieldtype for this field 		|
| allow_null     | `<boolean>` | Allow null as a value                      |
| multiple       | `<boolean>` | Allow more than one input                  |
| return_format | `object|id` | Return Format for this field              |
| add_term | `<boolean>` | Allow to add taxonomies              |
| save_terms | `<boolean>` | Allow to save taxonomies              |
| load_terms | `<boolean>` | Allow to load taxonomies              |


#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'taxonomy',
    'taxonomy' => 'category',
    'allow_null' => 0,
    'multiple' => 1,
    'return_format' => 'object',
    'add_term' => 0,
    'save_terms' => 0,
    'load_terms' => 0
  ]
?>
```



---



## User

Allows you to link a user to this field.

| name       | options     | description                      |
| :--------- | ----------- | -------------------------------- |
| role       | `<string>`  | User roles which can be selected |
| allow_null | `<boolean>` | Allow null as a value            |
| multiple   | `<boolean>` | Allow more than one input        |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'user',
	'role' => 'administrator',
    'allow_null' => 0,
    'multiple' => 1
  ]
?>
```



---



## Relationship

Allows you to create relationships with this field.

| name          | options   | description                 |
| :------------ | --------- | --------------------------- |
| post_type     | `<array>` | Array of post types allowed |
| taxonomy      | `<array>` | Array of taxonomies allowed |
| min           | `<int>`   | Minimum to select           |
| max           | `<int>`   | Maximum to select           |
| filters       | `<array>` | Filters Taxonomies          |
| elements      | `<array>` | Selected will be displayed in results |
| return_format | `object|id` | Return format for this field  |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'relationship',
	'post_type' => array('post', 'page'),
    'taxonomy' => array(),
	'min' => 0,
    'max' => 0,
    'filters' => array('search', 'post_type', 'taxonomy'),
    'elements' => array(
    	'featured_image' => 'Featured Image'
    ),
    'return_format' => 'object'
  ]
?>
```



---



## Post Object

Allows you to connect Post Objects with this field.

| name          | options   | description                 |
| :------------ | --------- | --------------------------- |
| post_type     | `<array>` | Array of post types allowed |
| taxonomy      | `<array>` | Array of taxonomies allowed |
| allow_null | `<boolean>`   | Allow null as a value |
| multiple | `<boolean>`   | Allow multiple selections |
| ui      | `<boolean>` | Use the ACF UI |
| return_format | `object|id` | Return format for this field  |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'post_object',
	'post_type' => array('post', 'page'),
    'taxonomy' => array(),
	'allow_null' => 0,
    'multiple' => 0,
    'ui' => 1,
    'return_format' => 'object'
  ]
?>
```



---



## Color Picker

A color picker which returns hexcodes

| name          | options    | description                      |
| :------------ | ---------- | -------------------------------- |
| default_value | `<string>` | The default value for this field |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'color_picker',
    'default_value' => '#ffffff'
  ]
?>
```



---



## Date Picker

A date picker which returns date formats

| name           | options    | description                                     |
| :------------- | ---------- | ----------------------------------------------- |
| display_format | `<string>` | Display format of the date                      |
| return_format  | `<string>` | The returned format of the date                 |
| first_day      | `<int>`    | The day number of the first day in the calendar |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'date_picker',
    'display_format' => 'd.m.Y',
    'return_format' => 'Y-m-d',
    'first_day' => 1
  ]
?>
```



---



## Date Time Picker

A date time picker which returns date formats

| name           | options    | description                                     |
| :------------- | ---------- | ----------------------------------------------- |
| display_format | `<string>` | Display format of the date                      |
| return_format  | `<string>` | The returned format of the date                 |
| first_day      | `<int>`    | The day number of the first day in the calendar |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'date_time_picker',
    'display_format' => 'd.m.Y H:i:s',
    'return_format' => 'Y-m-d g:i a',
    'first_day' => 1
  ]
?>
```



---



## Google Map

A google map field which returns lat, lang and the address

| name       | options    | description           |
| :--------- | ---------- | --------------------- |
| height     | `<string>` | Height in px          |
| center_lat | `<string>` | The start latitude    |
| center_lng | `<string>` | The start longitude   |
| zoom       | `<string>` | The google zoom level |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'google_map',
    'height' => '400',
    'center_lat' => '-37.81411',
    'center_lng' => '144.96328',
    'zoom' => '14'
  ]
?>
```


---



## Oembed

A oembed field which returns an iframe

| name   | options    | description  |
| :----- | ---------- | ------------ |
| height | `<string>` | Height in px |
| width  | `<string>` | Width in px  |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'oembed',
    'height' => '640',
    'width' => '390'
  ]
?>
```


---



## Time Picker

A timepicker field which returns an time format

| name           | options    | description                                     |
| :------------- | ---------- | ----------------------------------------------- |
| display_format | `<string>` | Display format of the time                      |
| return_format  | `<string>` | The returned format of the time                 |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'time_picker',
	'display_format' => 'H:i:s',
    'return_format' => 'H:i:s'
  ]
?>
```


---



## Message

Will show a message in the backend

| name           | options    | description                    |
| :------------- | ---------- | -------------------------------- |
| message | `<string>` | The message of the string |
| esc_html  | `<boolean>` | Should HTML be escaped |
| new_lines  | `wpautop|br|<none>` | What should happen with breaks |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'message',
	'message' => 'Hello World',
    'esc_html' => 1,
    'new_lines' => 'br'
  ]
?>
```


---



## Output

Will show a message in the backend

| name | options    | description        |
| :--- | ---------- | ------------------ |
| html | `<string>` | HTML of the output |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'output',
    'html' => '<p>Hello World</p>'
  ]
?>
```


---



## Tab

Will group everything below in a tab

| name | options    | description        |
| :--- | ---------- | ------------------ |
| placement | `top|bottom` | Placement of the Tab |
| endpoint | `<boolean>` | set this to the last tab |

#### Example

```php
<?php
  [
    'name' => 'my_field',
    'key' => 'my_field',
    'type' => 'tab',
    'placement' => 'top',
    'endpoint' => 0
  ]
?>
```


---

## Contribution

If you want to keep this up to date, send me a pull request with your change and a reference to the ACF repository change.
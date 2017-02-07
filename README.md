# ACF Unofficial API Field Documentation

This documentation will cover the ACF fields which are shipped with ACF and ACF Pro. Since the official documentation is missing field definitions
for PHP I wanted to add them for other developers using ACF without the Wordpress UI.



## Table of Contents

* **Fields**

  * *General Fields*

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

  * *File Upload Fields*

    * [Image](#image)
    * [File](#file)

  * *Wordpress Related Fields*

    * [Page Link](#page-link) (TODO)
    * [Taxonomy](#taxonomy) (TODO)
    * [User](#user) (TODO)
    * [Relationship](#relationship) (TODO)
    * [Post Object](#post-object) (TODO)

  * *Data Fields*

    * [Color Picker](#color-picker) (TODO)
    * [Date Picker](#date-picker) (TODO)
    * [Date Time Picker](#date-time-picker) (TODO)
    * [Google Map](#google-map) (TODO)
    * [Oembed](#oembed) (TODO)
    * [Time Picker](#time-picker) (TODO)

  * *Structure Fields*

    * [Message](#message) (TODO)
    * [Output](#output) (TODO)
    * [Tab](#tab) (TODO)

    ​

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
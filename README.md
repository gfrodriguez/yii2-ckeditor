# Yii2 CKEditor

This is a fork [MihailDev/yii2-ckeditor](https://github.com/MihailDev/yii2-ckeditor) and [sadovojav/yii2-ckeditor](https://github.com/sadovojav/yii2-ckeditor)

#### Features:
- The ability to add custom plugins
- Initialisation editor on event
- Added custom plugins 

Plugins:
- [Line Utilities](http://ckeditor.com/addon/lineutils)
- [Widget](http://ckeditor.com/addon/widget)
- [Enhanced Image](http://ckeditor.com/addon/image2)
- [Mathematical Formulas](https://ckeditor.com/addon/mathjax)
- [Word Count & Char Count Plugin](https://ckeditor.com/addon/wordcount)
- [Table Resize](https://ckeditor.com/addon/tableresize)
- Etc...

### Composer

The preferred way to install this extension is through [Composer](http://getcomposer.org/).

Either run ```php composer.phar require gfrodriguez/yii2-ckeditor "dev-master"```

or add ```"gfrodriguez/yii2-ckeditor": "dev-master"``` to the require section of your ```composer.json```

### Use

- Widget

```php
use gfrodriguez\ckeditor\CKEditor;

echo CKEditor::widget();
```

- ActiveForm

```php
use gfrodriguez\ckeditor\CKEditor;

echo $form->field($post, 'text_full')->widget(CKEditor::className());
```

#### Parameters
- array `editorOptions` - CKeditor options
- array `containerOptions` - Container options
- array `extraPlugins` - Extra plugins connection
- string `initOnEvent ` =  `false` - Event type for initialization

##### Example

```php
echo $form->field($post, 'text_full')->widget(CKEditor::className(), [
    'extraPlugins' => [
        ['test', '@root/uploads/plugins/test-plugin/', 'plugin.js']
    ],
    'editorOptions' => [
        'toolbar' => [
			['Preview', 'Viewss'],
			['Cut', 'Copy', 'Paste', 'PasteText', 'PasteFromWord', '-', 'Undo', 'Redo'],
			['Find', 'Replace', '-', 'SelectAll', '-', 'Scayt'],
			['Bold', 'Italic', 'Underline', 'Strike', 'Subscript', 'Superscript', 'TextColor', 'BGColor', '-', 'RemoveFormat'],
			['NumberedList', 'BulletedList', '-', 'Outdent', 'Indent', '-', 'Blockquote', '-', 'JustifyLeft', 'JustifyCenter', 'JustifyRight', 'JustifyBlock'],
			['Image', 'Table', 'SpecialChar', 'Mathjax'],// 'Footnotes'],
			['Styles', 'Format'],
			['Maximize', 'ShowBlocks'],
			['About'],
        ],
        'allowedContent' => true,
        'forcePasteAsPlainText' => true,
        'extraPlugins' => 'test,image2,widget,oembed,video',
        'language' => Yii::$app->language,
        'height' => 500,
		'mathJaxLib' => '//cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS_HTML',
        'disableNativeSpellChecker' => false,
        'scayt_sLang' => Yii::$app->language,
        'removePlugins' => 'scayt,wsc',
        'disableNativeSpellChecker' => false,
        'qtRows' => 8, // Count of rows in the quicktable (default: 8)
        'qtColumns' => 10, // Count of columns in the quicktable (default: 10)
        'qtBorder' => '1', // Border of the inserted table (default: '1')
        'qtWidth' => '90%', // Width of the inserted table (default: '500px')
        'qtCellPadding' => '0', // Cell padding of the inserted table (default: '1')
        'qtCellSpacing' => '0', // Cell spacing of the inserted table (default: '1')
        'qtPreviewSize' => '14px', // Cell size of the preview table (default: '14px')
        'qtPreviewBackground' => '#c8def4' // Cell background of the preview table on hover (default: '#e5e5e5')
    ],
]);
```

#### Initialisation editor on event
```
'initOnEvent' => 'focus' //dblclick, mouseover, etc.
```

#### Use extra plugins

1. Add extra plugin connection information
```
'extraPlugins' => [
    ['test', '@root/uploads/plugins/test-plugin/', 'plugin.js']
],
```

- `test` required - plugin name
- `@root/uploads/plugins/test-plugin/` required - path to plugin
- `plugin.js` required - plugin script file
  
2. Add extra plugin to editorOptions -> extraPlugins
```
'extraPlugins' => 'dialog,lineutils,wordcount,notification,image2,widget,oembed,quicktable,tableresize,filetools,notificationaggregator,mathjax',
```
Without space after comma.

3. If your plugin use the button, add it on the panel
```
'toolbar' => [
    ['test'],
],
```

### Links

- Mouse event - https://api.jquery.com/category/events/mouse-events/
- CKEditor Api - http://docs.ckeditor.com/
- File manager ElFinder - https://github.com/MihailDev/yii2-elfinder

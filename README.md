Generate image thumbnail ad-hoc for Yii2 project
===================================

Installation
----------
add
```
"ipoz/yii2-thumbnail": "@dev"
```

```
"repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/ipoz/yii2-fthumbnail"
    }
  ]
```

Configuration app
----------
```php
'components' =>
[
    'thumbnail' => [
        'class' => 'ipoz\yii2\fthumbnail\Thumbnail',
        'repositoryDir' => PATH_TO_YOUR_REPOSITORY
    ]

]
```

Usage
----------
```php
use ipoz\yii2\thumbnail\Image;

...

public function actionThumbnail($image, $width, $height = 0, $type = '')
    {
        $imagePath = \Yii::$app->fthumbnail ->generateThumbnail($image, $width, $height, $type);
        return \Yii::$app->response->sendFile($imagePath, $image, [
            'mimeType' => Image::getMimeType($imagePath),
            'inline' => true,
        ]);
    }
```
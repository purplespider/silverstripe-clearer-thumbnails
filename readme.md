# Clearer Thumbnails for Silverstripe

This module fixes an issue in Silverstripe 4 which results in particularly tall or wide images having pixelated/blurry thumbnails in the CMS, particularly for `UploadFields`.

It also increases the size of thumbnail images to ensure they remain crips on HiDPI/Retina displays.

## Installation

1. Install module via composer:
````
composer require purplespider/silverstripe-clearer-thumbnails
````
2. For sites with existing assets, run the generate-cms-thumbnails task to re-generate the thumbnails for the Files tab.
````
php vendor/silverstripe/framework/cli-script.php dev/tasks/MigrateFileTask generate-cms-thumbnails
````

## What does exactly does this do?

It simply overrides some settings via a config file to:
1. Change `ThumbnailGenerator` `$method` from `FitMax` to `Fill` which avoids thumbnails being generated too small and then stretched.
2. Doubles the `UploadField` `$thumbnail_width` and `$thumbnail_height` from `60` to `120` to ensure thumbnails are crisp on HiDPI/Retina displays.
3. Increases the `Image` `$asset_preview_width` and `$asset_preview_height` to ensure image previews in the Files area are crisp on HiDPI/Retina displays.
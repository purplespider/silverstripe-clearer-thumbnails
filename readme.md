# Clearer Thumbnails for Silverstripe

This module fixes an issue in Silverstripe 4 which results in particularly tall or wide images having pixelated/blurry thumbnails in the CMS, particularly for `UploadFields`.

Before:

<img width="591" alt="Screenshot 2021-08-06 at 09 24 31@2x" src="https://user-images.githubusercontent.com/329880/128480831-0e9bcbf2-e2f1-4b4d-a7ac-1ea93fdcee2b.png">

After:

<img width="585" alt="Screenshot 2021-08-06 at 09 29 37@2x" src="https://user-images.githubusercontent.com/329880/128481538-4e60c3b8-8a26-4042-979d-f4a0ad97a506.png">

It also increases the size of thumbnail images to ensure they remain crips on HiDPI/Retina displays.

## Installation

1. Install module via composer:
````
composer require purplespider/silverstripe-clearer-thumbnails
````
2. Perform a flush: 
````
https://www.example.com?flush=1
````
5. For sites with existing assets, run the generate-cms-thumbnails task to re-generate the thumbnails for the Files tab (otherwise no thumbnails will appear).
````
php vendor/silverstripe/framework/cli-script.php dev/tasks/MigrateFileTask generate-cms-thumbnails
````

## What exactly does this do?

It simply overrides some settings via a config file to:
1. Change `ThumbnailGenerator` `$method` from `FitMax` to `Fill` which avoids thumbnails being generated too small and then stretched.
2. Doubles the `UploadField` `$thumbnail_width` and `$thumbnail_height` from `60` to `120` to ensure thumbnails are crisp on HiDPI/Retina displays.
3. Increases the `Image` `$asset_preview_width` and `$asset_preview_height` to ensure image previews in the Files area are crisp on HiDPI/Retina displays.

## Updating

Any updates to this module which require the `generate-cms-thumbnails` task to be re-run will be tagged as a new major version. So when updating major versions please remember to do this.

# Hydrogen
Hydrogen - unofficial VK API PHP SDK.
# Installing
```
composer require maxgoody/hydrogen
```
# Usage
```php
<?php
require __DIR__.'/vendor/autoload.php';

use Hydrogen\Client;
use Hydrogen\Language;

$client = new Client(
    '45a14b2953ff9e35c58d0f8eb94076455534baf6edf78dc7018bd5d93d06029be83efd260cb3013b3a67e', // token, required
    '5.80', // verison, optional, default 5.92
    Language::ENGLISH // language, optional, default Language::RUSSIAN
);

// Call users.get method.
$response = $client->users->get();

print_r($response[0]);
/*
    Array
    (
        [id] => 124349821
        [first_name] => Maxim
        [last_name] => Alexeev
    )
*/

// Upload photo on wall.
$response = $client->photos->getWallUploadServer();
$response = $client->upload($response['upload_url'], 'photo', __DIR__.'/photo.jpg');
$response = $client->photos->saveWallPhoto($response);

print_r($response[0]);
/*
    Array
    (
        [id] => 456247530
        [album_id] => -10
        [owner_id] => 124349821
        [sizes] => Array
            (
                [0] => Array
                    (
                        [type] => s
                        [url] => https://pp.userapi.com/c844416/v844416147/1c2096/PqfUGS07qL4.jpg
                        [width] => 50
                        [height] => 75
                    )

                [1] => Array
                    (
                        [type] => m
                        [url] => https://pp.userapi.com/c844416/v844416147/1c2097/L-c7Q35yQ_U.jpg
                        [width] => 87
                        [height] => 130
                    )

                [2] => Array
                    (
                        [type] => x
                        [url] => https://pp.userapi.com/c844416/v844416147/1c2098/tOfqtCYJtUE.jpg
                        [width] => 403
                        [height] => 604
                    )

                [3] => Array
                    (
                        [type] => y
                        [url] => https://pp.userapi.com/c844416/v844416147/1c2099/mTJ5xgBSVdI.jpg
                        [width] => 539
                        [height] => 807
                    )

            )

        [text] =>
        [date] => 1552496585
        [access_key] => a238bdg91ccf770203
    )
*/
```

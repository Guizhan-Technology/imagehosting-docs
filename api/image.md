# Image

An image is an object that describes the uploaded image.

## Object definition :id=def

View properties and constraints defined on the object

<details>
<summary>Definition</summary>

**Example object**

```json
{
    "name":"HNxEE3W",
    "fullname":"HNxEE3W.jpeg",
    "size":24902,
    "upload_time":"2021-01-09T17:52:03.000000Z",
    "url":"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"
}
```

|Name */type*|Description */example*|Constraints|
|-|-|-|
|**name**<br>*string*|The name of image <br>`"HNxEE3W"`|read only|
|**fullname**<br>*string*|The fullname of image <br> `"HNxEE3W.jpeg"`|read only|
|**size**<br>*integer*|The size of image <br> `24902`|read only|
|**upload_time**<br>*datetime*|The upload time <br> `"2021-01-09T17:52:03.000000Z"`|read only|
|**url**<br>*string*|The URL of the image <br> `"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"`|read only|

</details>

## List Images :id=list

List, search, and sort your images

```
GET images
```

*Parameters*

|Name */type*|Description */example*|Constraints|
|-|-|-|
|page<br>*integer*|*Optional*<br>Page number of paginated results<br>`1`|default value: 1<br>min value: 1|
|per_page<br>*integer*|*Optional*<br>Number of images per page<br>`10`|default value: 10<br>min value: 5<br>max value: 20|
|order<br>*string*|*Optional*<br>Field to order images by<br>`size`|valid values: name, size, upload_time|
|direction<br>*string*|*Optional*<br>The direction to order<br>`desc`|valid values: ASC, DESC|

**Response** (example)

```json
{
    "code": 0,
    "message": null,
    "result": [
        {
            "name":"HNxEE3W",
            "fullname":"HNxEE3W.jpeg",
            "size":24902,
            "upload_time":"2021-01-09T17:52:03.000000Z",
            "url":"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"
        }
    ]
}
```

## Upload Image :id=upload

```
POST images
```

*Parameters*

|Name */type*|Description|Constraints|
|-|-|-|
|image<br>*binary*|*Optional*<br>The binary information of image|Cannot be empty if `image_base64` is empty|
|image_base64<br>*string*|*Optional*<br>Base64 encoded information of image|Cannot be empty if `image` is empty|

**Response** (example)

```json
{
    "code": 0,
    "message": null,
    "result": {
        "name":"HNxEE3W",
        "fullname":"HNxEE3W.jpeg",
        "size":24902,
        "upload_time":"2021-01-09T17:52:03.000000Z",
        "url":"https:\/\/gzimg.cc\/21w01\/HNxEE3W.jpeg"
    }
}
```
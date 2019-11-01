# react-native-fecth-blob
This repository has been archived by the owner. Because of these we are using [rn-fecth-blob](https://github.com/joltup/rn-fetch-blob) library forked by [joltup](https://github.com/joltup).

## Why we are using?
We are using this library for services response and sending large files(video, image etc.)

## Where we are using?
We are using under utils and services folders in our projects.
> For Example: app > services > serviceUtils.js

## How we are using?

```javascript
    <!-- app > services > serviceUtils.js -->

    import RNFetchBlob from 'rn-fetch-blob';


    const Fetch = RNFetchBlob.polyfill.Fetch;

    const myFetch = new Fetch({
        // enable this option so that the response data conversion handled automatically
        auto: false,
        trusty: false,
        // when receiving response data, the module will match its Content-Type header
        // with strings in this array. If it contains any one of string in this array,
        // the response body will be considered as binary data and the data will be stored
        // in file system instead of in memory.
        // By default, it only store response data to file system when Content-Type
        // contains string `application/octet`.
        binaryContentTypes: [
            'image/',
            'video/',
            'audio/',
            'foo/',
        ]
    }).build();

    GLOBAL.tmpFetch = myFetch;
    GLOBAL.fetch = function (uri, options, ...args) {
        return GLOBAL.tmpFetch(uri, options, ...args).then((response) => {
            return response;
        });
    };
```
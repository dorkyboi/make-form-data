# make-form-data
Helper function that recursively turns plain JS object into FormData instance

## Installation
npm: `npm i make-form-data`

yarn: `yarn add make-form-data`

## Usage
Function handles your data recursively, which means you can mix-and-match your values and nest them however you need to.
```javascript
import makeFormData from "make-form-data";

const data = {
    // supports arrays
    favours: [
        'coding',
        {
            type: 'activity',
            name: 'snowboarding',
        },
        'serfing',
    ],
    
    // supports objects
    images: {
        some: 'object',
        info: 'here',
    },
    
    // supports File instances
    file: new File(['some file contents'], 'my-text-file.txt'),

    // booleans turn into '1' or empty string
    truthyBoolean: true, // => '1'
    falsyBoolean: false, // => ''

    // null values also turn into empty strings
    nullable: null, // => ''

    /**
     * Everything else is handled by FormData.append()
     * @see https://developer.mozilla.org/en-US/docs/Web/API/FormData/append
     */
};

const formData = makeFormData(data);
```

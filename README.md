# crc32-browser

Calc CRC32 for local file on browser.

Use HTML5 and ES6 style.

## run in browser

Import crc32.js from script tag. like `<script src="crc32.js"></script>` 

```javascript
//init crc32 object. Each Crc32 object can only calc one file.
var crc32 = Crc32();
//get the file which user selected.
var file = $("#file-input")[0].files[0];
//get crc32 result
var callback = function(crc32){
    console.log(crc32);
}

var fileReader = new FileReader();
fileReader.readAsArrayBuffer(file);
fileReader.onload = function(e) {
    crc32.update(e.target.result);

    if(/* file read finish */){
        callback(crc32.digest())
    }
};
fileReader.onerror = function() {
    //on error code
};
```

## method

**Class Crc32**

Init a crc32 calc for one file.

**update(data)**

update crc32 from filedata or one piece of file data blob.

**digest(base)**

get the value of crc32

base: default: 16  get crc32 value in hex.

2, 8, 10, 16 can be passed here.
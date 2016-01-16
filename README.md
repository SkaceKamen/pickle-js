# js pickle

"Simple" module allowing you to decode pickle encoded data using javascript

## Example
Load from array or string
```js
//Original: [1, 2, [3, 4], { (abc,5): "def" }]
var pickled = [40,108,112,48,10,73,49,10,97,73,50,10,97,40,73,51,10,73,52,10,116,112,49,10,97,40,100,112,50,10,40,83,39,97,98,99,39,10,112,51,10,73,53,10,116,112,52,10,86,100,101,102,10,112,53,10,115,97,46],
    buff = new ArrayBuffer(pickled.length),
    view = new Uint8Array(buff),
    data = null;

//Copy pickled into buffer
for(var i in pickled)
    view[i] = pickled[i];

//Parse pickled data
data = pickle.load(buff);
//data = [1, 2, [3, 4], { "abc,5": "def" }]
``` 

Load from file
```js
var xhr = new XMLHttpRequest();
xhr.open('GET', "NRXWO2LOFVRXILTXN5ZGYZDPMZ2GC3TLOMXG4ZLUHIZDAMBRGU5VG23BMNSUWYLDNBXGCX2FKU======.dat", true);
//Important, wont get mixed up with UTF-8 stuff
xhr.responseType = 'arraybuffer';
xhr.onload = function(e) {
    console.log(pickle.load(xhr.response));
};
xhr.send();
``` 

HTML5 Storage
=============
HTML5 Storage takes advantage browser localStorage by applying a safe and powerful wrapper to it.

Features
--------
- Detect and plan for non-supported localStorage browers.
- Store and load objects from localStorage.
- Catches localStorage errors to allow for cleaner code.
- No javascript library dependencies.

How To Use
----------
Just include storage.js into your project and you are ready to being using it.  Here is an example.

    var run = function() {
        var myPoint = {x: 3, y: 2, info: {name: "point"}};
        Storage.save("point", myPoint);
        
        console.log(Storage.size());
        
        var myPoint2 = Storage.load("point");
        console.log(myPoint2.info.name);
        
        Storage.remove("point");
        var myPoint3 = Storage.load("point");
        
        if(myPoint3 === null) {
            console.log("There is not 'point' in localStorage");
        }
        
        Storage.clear();
        console.log(Storage.size());
    };
    
    var die = function() {
        alert("This browser does not support localStorage.");
    };

    Storage.isSupported(run, die);

API
---
> **clear()** <br/><br/>
`return - True if localStorage is cleared, false if localStorage is not supported.` <br/>

Removes all data from localStorage.

---

> **isSupported( success, error )** <br/><br/>
`param success - Callback function that is triggered if localStorage is supported by browser.` <br/>
`param error - Callback function that is triggered if localStorage is not supported by browser.` <br/>
`return - True if localStorage is supported, false if not.`

Determines if the current browser supports localStorage

---

> **load( key )** <br/><br/>
`param key - The key to load data from in localStorage.` <br/>
`return - The data in localStorage (primitive and object), null if no data is found.` <br/>

Loads data from the localStorage (primitives and objects).

---

> **remove( key )** <br/><br/>
`param key - The key to delete from localStroage.` <br/>
`return - True if the data is found and removed, false if not removed or not found.`

Removes data from localStorage.

---

> **save( key, data )** <br/><br/>
`param key - The key data will be saved under in the localStorage.` <br/>
`param data - The data to be saved to localStorage (primitives or objects).` <br/>
`return - True is data is saved successfully, false if not.`

Saves data to localStorage (primitives and objects).

---

> **size()** <br/><br/>
`return The number of elements currently in localStorage, 0 if localStorage is not supported.`

Gets the number of items currently being stored in localStorage.

---

License
-------
- [MIT](http://www.opensource.org/licenses/mit-license.php)
# SecureDB - An encrypted and secure database

## Installation

```
$ npm install secure-db
```

## Documentation

### Methods

* [.add(data_name, value)](#add-method)
* [.all()](#all-method)
* [.delete(data_name)](#delete-method)
* [.get(data_name)](#get-method)
* [.has(data_name)](#has-method)
* [.push(data_name, element)](#push-method)
* [.reset()](#reset-method)
* [.set(data_name, value)](#set-method)
* [.splice(data_name, value)](#splice-method)
* [.sub(data_name, number)](#sub-method)
* [.sum(data_name, number)](#sum-method)

<h3 id="add-method">.add(data_name, value)</h3>

```javascript
const db = require("secure-db")();

// Add a string or a number in front of the existing value.

db.set("name", "Jhon");
db.add("name", " Simon");
// name === "Jhon Simon"

db.set("count", 12);
db.add("count", 49);
// count === "1249"
```

<h3 id="all-method">.all()</h3>

```javascript
const db = require("secure-db");

// Returns all existing data.

db.set("my_money", 1000);
db.set("my_car", "Ferrari");
db.set("members", 24);

var data = db.all();
// data === { my_money: 1000, my_car: "Ferrari", members: 24 }

var my_items = db.all({startsWith: "my"});
// my_items === { my_money: 1000, my_car: "Ferrari" }
```

<h3 id="delete-method">.delete(data_name)</h3>

```javascript
const db  require("secure-db")();

// Completely deletes some data that has been stored.

db.set("my_money", 1000);
db.set("my_car", "Ferrari");
db.set("members", 24);

var data = db.all()
// data === { my_money: 1000, my_car: "Ferrari", members: 24 }

db.delete("my_car");

var data = db.all()
// data === { my_money: 1000, members: 24 }
```

<h3 id="get-method">.get(data_name)</h3>

```javascript
const db = require("secure-db")();

// Returns data for an element.

db.set("my_car", "Ferrari");
db.set("members", 24);

const car = db.get("my_car");
// car === "Ferrari";

const money = db.get("my_money");
// money === null || undefined;
```

<h3 id="has-method">.has(data_name)</h3>

```javascript
const db = require("secure-db")();

// Checks if a data exists and returns a boolean.

db.set("my_money", 1000);
db.set("my_car", "Ferrari");
db.set("members", 24);

db.has("members");
// true

db.has("shop");
// false
```

<h3 id="push-method">.push(data_name, element)</h3>

```javascript
const db = require("secure-db")();

// Adds an element if the data value is of type array.

db.set("names", ["Sabrina", "Mike", "Jhosh"]);

db.push("names", "Nic");
var names = db.get("names");
// names === ["Sabrina", "Mike", "Jhosh", "Nic"]

db.set("blacklist", []);

db.push("blacklist", "Felipe_");
var bl = db.get("blacklist");
// bl === ["Felipe_"];

db.push("blacklist", "VK");
bl = db.get("blacklist");
// bl = ["Felipe_", "VK"]
```

<h3 id="reset-method">.reset()</h3>

```javascript
const db = require("secure-db")();

// Deletes all data from the database.

db.set("my_money", 1000);
db.set("my_car", "Ferrari");
db.set("members", 24);

var data = db.all()
// data === { my_money: 1000, my_car: "Ferrari", members: 24 }

db.reset();

data = db.all();
// data === {}
```

<h3 id="set-method">.set(data_name, value)</h3>

```javascript
const db = require("secure-db")();

// Defines a new value for the data excluding the previous one.

db.set("money", 1000);
var money = db.get("money");
// money === "1000"

db.set("money", 50);
money = db.get("money");
// money === "50"
```

<h3 id="splice-method">.splice(data_name, value)</h3>

```javascript
const db = require("secure-db")();

// Removes an element from an array.

db.set("names", ["Sabrina", "Mike", "Jhosh"]);

db.push("names", "Nic");
var names = db.get("names");
// names === ["Sabrina", "Mike", "Jhosh", "Nic"]

db.splice("names", "Mike");
names = db.get("names");
// names === ["Sabrina", "Jhosh", "Nic"]
```

<h3 id="sub-method">.sub(data_name, number)</h3>

```javascript
const db = require("secure-db")();

// Subtract a number from the existing value.

db.set("money", 1000);
var money = db.get("money");
// money === "1000"

db.sub("money", 200);
money = db.get("money");
// money === "800"
```


<h3 id="sum-method">.sum(data_name, number)</h3>

```javascript
const db = require("secure-db")();

// Adds a number with an existing value. 

db.set("money", 1000);
var money = db.get("money");
// money === "1000"

db.sum("money", 875);
money = db.get("money");
// money === "1875"
```


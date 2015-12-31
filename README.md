# aix-mongo

Node.js module for managing mongodb ( [Developed With Love at Aixsystem core development department](http://www.aixsystem.com/) )

This is a module that you can easily manage your mongodb database for inserting, updating, finding or removing your documnets.

If there is any problem or if you think it's better to update or add another functionality to the module please let me know, and help me to improve this simple and small package.

## Installation

```sh
$ npm install aix-mongo
```

## Usage

```js
var db = require('aix-mongo');
```

### Adding ang important option
```js
db.init({dbAddress: "mongodb://localhost:27017/Your-database-name"});
```
Where your-database-name is your db.

### Usage
Usage of `aix-mongo` is very simple. There is just a few functions.

#### Converting string id to an object id
```js
db.objId(string);
// Usage example in a remove function.
db.update("clients", {_id:db.objId(req.body.id)}, function(){
    console.log("Client removed!");
});
// Or handy write and id
db.update("clients", {_id:db.objId("56798c9b4a2572512542145f")}, function(){
    console.log("Client removed!");
});

```

#### Finding a document/s
```js
db.find("collection-name", [filters], function(result){
    // your code goes here.
});
```
##### Example:
All parameters in [] are optional. 
Resutls are as arrays of objects.
```js
db.find("collection-name", {name:"john", lname:"kangari"}, function(result){
    console.log(result[0].email);
    // Result: john.kangari@gmail.com
});
```

#### Insert document into collection
```js
db.ins("collection-name", {data}, function(result){
    // your code goes here.
});
```

#### Update document/s
```js
db.update("collection-name", {credential}, {new-data}, function(result){
    // your code goes here.
});
// Example with result:
db.update("clients", {name:"john"}, {email:"example@domain.com"}, function(result){
    console.log(result.nModified);
// Result: 1
});

// Example with result function:
db.update("clients", {name:"john"}, {email:"example@domain.com"}, function(){
    console.log("Update done successfully.");
});

// Example without any function:
db.update("clients", {name:"john"}, {email:"example@domain.com"});
```
#### Remove a document/s
```js
db.remove("collection-name", {filters}, function(){
    // Your code goes here...
});
//Simple example of usage
db.remove("clients", {name:"john"}, function(){
    console.log("The client removed.");
});
```
This is a quick start documentation, if any more detail needed please refer to the `GitHub` page and let me know.

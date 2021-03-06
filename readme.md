## Cargo ##

A small key value store abstraction that you can use on the server in analogy of html5 localstorage and also on the client.

### Simple usage ###

It has the same interface as of localstorage.

Just make an instance of Storage.
```dart
Cargo storage = new Cargo();
```

Then you will have an asynchronous method to say that the storage is started

```dart
Cargo storage = new Cargo(MODE: CargoMode.FILE, conf: { "path" : "../store/" });
  
storage.start().then((_) {
  // do storage operations
  
});
```
Add data to the storage.
```dart
storage.setItem("data", {"data": "data"});
storage["data"] = {"data": "data"};
```	
Retrieve data from the storage on an asynchronous way.
```dart
var data = storage.getItem("data");
```
Or on a synchronous way.
```dart
var data = storage["data"];
```
Or like this	
```dart	
var data = storage.getItemSync("data");
```	
Realtime data events are possible as follow.
Adding events responds immediately to data changes as they occur. 
```dart
cargo.on("userData", (DataEvent de) {
	// add code that needs to happen when userData value is been changed
	
});
```
You can also turn the event off!
```dart
cargo.off("userData", dataChangeListener);
```
Or remove all the listeners
```dart
cargo.offAll("userData");
```	
You can also listen to all the data changes.
```dart
cargo.onAll((DataEvent de) => print(de));
```
A DataEvent consist out of a key, a value and a data type (changed, removed).
	
These are the modes that you can use:

Serverside:

	CargoMode.MEMORY
  	CargoMode.FILE

Clientside:

	CargoMode.MEMORY
  	CargoMode.INDEXDB
  	CargoMode.LOCAL
  	CargoMode.SESSION
  	
You can also provide a defaultValue when you want to retrieve a value, but the value is not yet present.
```dart
cargo.getItem("key", defaultValue: new List());
```	
When you want to copy some data from one cargo implentation to another you can use.
```dart
cargo.copyTo(anotherCargoImpl);
```	
You can also export the data to a map with the functions export and exportSync.

You can add parameters, to export only that data that falls under these rules.
```dart
Map params = new Map();
params['point'] = 1;
params['date'] = date2;

cargo.export(params: params);
```
It is also possible to provide some options to the export.
```dart
Options options = new Options(limit: 3);
  
cargo.export(options: options);
```	
### Note ###

IndexDB is not fully functional, we are waiting on the 'await' keyword of dart.

### Contributing ###
 
If you found a bug, just create a new issue or even better fork and issue a
pull request with you fix.

### Join our discussion group ###

[Google group](https://groups.google.com/forum/#!forum/dart-force)

### Social media ###

#### Twitter ####

Follow us on twitter https://twitter.com/usethedartforce

#### Google+ ####

Follow us on [google+](https://plus.google.com/111406188246677273707)

or join our [G+ Community](https://plus.google.com/u/0/communities/109050716913955926616) 

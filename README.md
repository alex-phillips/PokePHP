# PokePHP

This is a PHP wrapper for the Pokemon API at http://PokeAPI.co/. You can use this wrapper
to retrieve information regarding abilities, descriptions, egg groups, games, moves,
pokemon, types, and retrieve sprite images for each Pokemon.

## API Usage

Paul Hallett (http://phalt.co/) has been AWESOME enough to build such an extensive and useful REST
API that is free to use. However, for good reason, there is the limitation of 300
requests PER RESOURCE PER DAY. This means you can request the 'mew' Pokemon object
300 times per day before you are cut off. However, each object contains a 'modified'
cariable that contains a formatted date of the last time the object was udpated in
the API. This is extremely useful for caching purposes. So please be courteous and take
advantage of this and build some sort of caching mechanism if you plan on continueous
and/or heavy use of this wrapper.

## Basic Usage

Usage is extremely easy. Simply require or include the PokemonAPI.php file in
your project and from there you can start calling constructors for any type
in the following manner.

Ex:
```php
$mew = new \PokemonAPI\Pokemon(151);
```

## Constructing New Objects

Each object is constructed the same way - by instantiating a new instance of the
object and passing the ID into the constructor. In the case of a new Pokemon object,
you can also pass in a string of the Pokemon's name.

Ex:
```php
$swords_dance = new \PokemonAPI\Move(14);

$squirtle = new \PokemonAPI\Pokemon('squirtle');
$cloyster = new \PokemonAPI\Pokemon(91);
```

## Getting an Object's Information

Although every object's variables are public, each object has 'getter' methods for
each parameter. It is highly recommended to use the getter methods instead of referencing
each variable directly since any variable that is related to another Pokemon API object
is constructed when calling the getter function.

Ex:
```php
$mew = new \PokemonAPI\Pokemon('mew');

// Returns array of stdClasses containing name, resource_uri, and resource_id
$types = $mew->types;

// This returns an array of Type objects
$types = $mew->getTypes();
```

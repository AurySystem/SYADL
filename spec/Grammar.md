# Grammar and compenents

Indents must be uniform although a file. 
``` yaml
(tpye) nest1 data="why":
  nest2: #(2 spaces 1 indent)
    nest3: none #(4 spaces 2 indents)
  
  stillnested: "g" #(2 spaces 1 indent)
   invalidnest: "badline" #(3 spaces 2 indents, invalid becuase the second indent is too short)

```

## Identifiers ( ect  ):

An idenitifier is a string of uinicode characters used as a key in a dictionary or to identify a node, it ends at a whitespace character
``` yaml
anIdentifer:
```

## Nodes etc type=bool name=etc:
A node is effectively an identifier value pair, but with additional options.
Anything on the left side of the seperator ":" that isn't the identifier is a "header" or "properties" which is an internal list/dictionary of values, both of the kind that specific data for the parser and user user type data.
``` yaml
(type) nest1 data="why" id="globalIdentifier" copy="otherId"#*or type*# num=5: "child"
```
``` json
{
  "nest1": {
    "properties": {"id": "globalIdentifier", "copy":"otherId", "data":"why", "num":5},
    "type": "type",
    "children": ["child"]
  }
}
```
As you can see the properties are an inline dictionary/assosative array, and an optional global id so this can be target by other nodes so it's properties can be inherited, and an copy key to indecate to the parser where this should copy in properties this doesn't overwrite from.

Propertyless nodes (also know as headerless nodes) are direct key value pairs such as:
``` yaml
key: "value"
```
``` json
{"key":"value"}
```
Most "Nodes" are headerless, as every value is a headerless node inserted directly into the tree of another node

## Child inheritance <xyz>
  
nodes (headered or headerless) can inherit children from other nodes.
to make building from templates and such easier. Uses control Characters and global keys on identifiers
``` yaml
^Dict: 
  key: "here"
  title: "a title"
  place: "anywhere"

<Dict>home:
  place: "home"
  world: "mine"

^List: 
  - 2
  - 5
  - 6

<List>why:
  - 3
```
``` json
{
  "home":{
    "place":"home",
    "world":"mine",
    "key":"here",
    "title":"a title"
  },
  "why":[
    3,
    5,
    6
  ]
}
```

## Dictionaries { why: "here" }
A dictionary is a series of identifier value pairs deliminated by whitespace either ecapsulated by ```{}``` or tab indented whitespace.

## Lists ["so" "many" "things"]


## References ${otherfield}
A reference is an encapsulated identifier that is replaced with the field matching the identitfier, refrences 

## Operations (+ - * / %)
operations combine values with other set values or refrences, operations run left to right without order of operations
"+" adds a string or number together
"-" subtracts a number or attempts to remove part of a string

## Booleans (True/False)
True/ False unencapsulated

## Numbers (Integers, Floating point numbers)


## Strings ("aaa")
always encapsulated by quotation marks

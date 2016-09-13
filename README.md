# juggle
A tiny language designed for use in text documents.

## spec
Juggle's syntax is designed to be minimally invasive, simply by taking up only 1 line and a small amount of space.
Juggle works by looking for two-character actions at the start of a line. These actions are:

```
#@ - denotes a global command
#? - denotes a boolean
## - denotes a comment (will be removed from final output)
#! - denotes a bang, a command which modifies the next line
```

For example, here's a text file using Juggle:

```
#?Unavailable

#!Upper
Lorem ipsum...
```

We call parse(input, options) on this with an input object as so:

```
{
  "upper": function(line) {
    return line.toUpperCase()
  }
}
```
(We don't need to do this when actually using Juggle, as an "upper" bang is provided by default)

Parsing would then return an object with the following structure:

```
{
  "result": "\nLOREM IPSUM...",
  "bools": {
    "unavailable": true
  }
}
```

Note how any Juggle lines are removed from the final output.

## parsers
Currently, a parser written in JavaScript is in pre-alpha, with more languages to come. If you want to contribute by writing a parser in your language of choice, you may do so once I've fleshed out the spec.

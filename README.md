# ChavaScript Parser

A tokenizer/parser for the ChavaScript language, forked from [acorn](https://github.com/acornjs/acorn).

## Installation

```sh
npm install chavascript-parser
```

## Usage

```javascript
const chsParser = require("chavascript-parser");

var code = `
יכולת אחד() {
   יהי א = 12;
   בקרה.תעד(א);
}
`;
const ast = chsParser.parse(code);
console.log(JSON.stringify(ast, null, "  "));
```

would produce the following abstract syntax tree:
```
{
  "type": "Program",
  "start": 0,
  "end": 50,
  "body": [
    {
      "type": "FunctionDeclaration",
      "start": 1,
      "end": 49,
      "id": {
        "type": "Identifier",
        "start": 7,
        "end": 10,
        "name": "ahd"
      },
      "expression": false,
      "generator": false,
      "async": false,
      "params": [],
      "body": {
        "type": "BlockStatement",
        "start": 13,
        "end": 49,
        "body": [
          {
            "type": "VariableDeclaration",
            "start": 18,
            "end": 29,
            "declarations": [
              {
                "type": "VariableDeclarator",
                "start": 22,
                "end": 28,
                "id": {
                  "type": "Identifier",
                  "start": 22,
                  "end": 23,
                  "name": "a"
                },
                "init": {
                  "type": "Literal",
                  "start": 26,
                  "end": 28,
                  "value": 12,
                  "raw": "12"
                }
              }
            ],
            "kind": "let"
          },
          {
            "type": "ExpressionStatement",
            "start": 32,
            "end": 47,
            "expression": {
              "type": "CallExpression",
              "start": 32,
              "end": 46,
              "callee": {
                "type": "MemberExpression",
                "start": 32,
                "end": 43,
                "object": {
                  "type": "Identifier",
                  "start": 32,
                  "end": 39,
                  "name": "console"
                },
                "property": {
                  "type": "Identifier",
                  "start": 40,
                  "end": 43,
                  "name": "log"
                },
                "computed": false
              },
              "arguments": [
                {
                  "type": "Identifier",
                  "start": 44,
                  "end": 45,
                  "name": "a"
                }
              ]
            }
          }
        ]
      }
    }
  ],
  "sourceType": "script"
}
```
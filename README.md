# MWE for tree-sitter wildcard match problem

The problem is a query of the general from `(_, (_))` returns unexpected matches. 

The problem is observed in version 0.20.8, but not in 0.20.7.

To reproduce:

    npm install # sometimes takes a while
    npx tree-sitter query queries.scm test.js

The output shows eight matches, among which the following two:

  pattern: 0
    capture: 1 - parent, start: (0, 0), end: (0, 10), text: `// test.js`
    capture: 0 - child, start: (2, 4), end: (2, 15), text: `answer = 42`
  pattern: 0
    capture: 1 - parent, start: (2, 0), end: (2, 16), text: `let answer = 42;`
    capture: 0 - child, start: (2, 4), end: (2, 15), text: `answer = 42`

The second one of these is correct, but the first one is not.

To try with other versions, change the `tree-sitter-cli` version in `package.json`.

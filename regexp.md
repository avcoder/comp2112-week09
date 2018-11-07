# Regex

```js
/a/.test("a"); //true
/a/.test("b"); //false

// see https://medium.freecodecamp.org/regular-expressions-demystified-regex-isnt-as-hard-as-it-looks-617b55cf787
```

1. Start Small with letters

```js
/a/.test("abc"); //true
/a/.test("bcd"); //false
/a/.test("cba"); //true
```

```js
let e = /a/;
e.test("abc"); //true
e.test("bcd"); //false
e.test("cba"); //true
```

1. Multi-Characters

```js
/ab/.test("abacus"); //true
/bac/.test("abacus"); //true
/abc/.test("abacus"); //false
/abas/.test("abacus"); //false
```

1. Numbers

```js
e = /[0-9]/;
e.test(42); //true
e.test("42"); //true
e.test("The answer is 42"); //true!
```

- But notice how the last test doesn't work
- It's because it matches numeric characters somewhere within the string
- But we need a search from start to end.

1. ^ and $

- ^ means the start of the string.
- $ means the end of the string

```js
/^a/.test("abc"); //true
/^a/.test("bca"); //false
/^http/.test("https://pineboat.in"); //true /^http/.test("ftp://pineboat.in"); //false

/js$/.test("regex.js"); //true
/js$/.test("regex.sj"); //false

let e = /^[0-9]$/;
e.test("42"); //false - NO!
e.test("The answer is 42"); //false
e.test("7"); //true
```

- '?' means I can see none or just one
- '+' means I need to see at least one or more
- '\*' means I can see none, one or more

```js
/a?/.test(""); //true
/a?/.test("a"); //true
/a?/.test("b"); //true!
/a?/.test("aa"); //true
/^a?$/.test("aa"); //false because It looks for zero or one a, start to end, nothing more, nothing less

/a+/.test("a"); //true
/a+/.test("aa"); //true
/a+/.test("ba"); //true!
/^a+$/.test("aa"); //true
/a+/.test(""); //false
/a+/.test("b"); //false
/^a+$/.test("ab"); //false because looks for 'a' start to end, no other characters allowed.

/a*/.test("a"); //true
/a*/.test("aa"); //true
/a*/.test("ba"); //true
/a*/.test(""); //true
/a*/.test("b"); //true
/^a*$/.test("aa"); //true
/^a*$/.test(""); //true
/^a*$/.test("ab"); //false
```

Answer for e.test("The answer 42")

```js
//Let's throw in a plus
let e = /^[0-9]+$/;
e.test("4"); //true
e.test("42"); //true
e.test("The answer 42"); //false - Hurray
```

- see http://library.georgiancollege.ca/barrie_hours#s-lg-box-10675402 where I
  use regular expressions via replace( .. ) method

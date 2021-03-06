# Phonewords

Two-way number-letter conversion as found on most phone dialers, according to [ITU-T E.161](https://en.wikipedia.org/wiki/E.161).

## Usage

Install the library:

```
npm install --save phonewords
```

Require the module and call one of its functions, depending on the desired direction of conversion:

```javascript
let phonewords = require('phonewords');
```

### Numbers to Words

Convert a number to an array of possible character combinations:

```javascript
phonewords.numbersToWords(2);
// => [ 'A', 'B', 'C' ]

phonewords.numbersToWords('2');
// => [ 'A', 'B', 'C' ]

phonewords.numbersToWords(22);
// => [ 'AA', 'AB', 'AC', 'BA', 'BB', 'BC', 'CA', 'CB', 'CC' ]

phonewords.numbersToWords(210);
// => [ 'A__', 'B__', 'C__' ]

phonewords.numbersToWords('+1 (201) ...');
// => [ '_A__', '_B__', '_C__' ]
```

Because `0` and `1` do no correspond to any characters, they are replaced with underscores.

Note that this function has a quadratic time complexity with respect to the number of input digits and should not be used for especially long numbers.


### Words to Numbers

Convert a string to a number:

```javascript
phonewords.wordstoNumbers('phonewords');
// => '7466396737'

phonewords.wordstoNumbers('pHoNewoRDs');
// => '7466396737'

phonewords.wordstoNumbers('P H O N E W O R D S');
// => '7466396737'

phonewords.wordstoNumbers('ph0new0rd5');
// => '7406390735'

phonewords.wordstoNumbers('!@#$%^&*()');
// => ''
```

Spaces and special characters are removed.  Numerals are left unchanged.

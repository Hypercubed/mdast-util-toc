# mdast-util-toc [![Build Status][build-badge]][build-status] [![Coverage Status][coverage-badge]][coverage-status]

Generate a Table of Contents from a [**mdast**][mdast] tree.

## Installation

[npm][]:

```bash
npm install remark-toc
```

**mdast-util-toc** is also available as an AMD, CommonJS, and globals
module, [uncompressed and compressed][releases].

Dependencies:

```javascript
var remark = require('remark');
var toc = require('mdast-util-toc');
```

Transform:

```javascript
var file = remark().parse(([
    '# Alpha',
    '',
    '## Bravo',
    '',
    '### Charlie',
    '',
    '## Delta',
    ''
].join('\n'));
```

Yields:

```markdown
-   [Alpha]

    -   [Bravo](#bravo)

        -   [Charlie](#charlie)

    -   [Delta](#delta)
```

## API

### `toc(node[, options])`

Generate a Table of Contents from a Markdown document.

*   Looks for the first heading containing `"Table of Contents"`, `"toc"`,
    or `table-of-contents` (case insensitive, supports alt/title attributes
    for links and images too);

*   Removes all following contents until an equal or higher heading is found;

*   Inserts a list representation of the hierarchy of following headings;

*   Adds links to following headings, using the same slugs as GitHub.

#### `options`

*   `heading` (`string?`)
    — Heading to look for, wrapped in `new RegExp('^(' + value + ')$', 'i');`

*   `maxDepth` (`number?`, default: `6`)
    — Maximum heading depth to include in the table of contents,
    This is inclusive, thus, when set to `3`, level three headings,
    are included (those with three hashes, `###`);

*   `tight` (`boolean?`, default: `false`)
    — Whether to compile list-items tightly.

## License

[MIT][license] © [Jonathan Haines][author]

<!-- Definitions -->

[build-badge]: https://img.shields.io/travis/BarryThePenguin/mdast-util-toc.svg

[build-status]: https://travis-ci.org/BarryThePenguin/mdast-util-toc

[coverage-badge]: https://img.shields.io/codecov/c/github/BarryThePenguin/mdast-util-toc.svg

[coverage-status]: https://codecov.io/github/BarryThePenguin/mdast-util-toc

[releases]: https://github.com/BarryThePenguin/mdast-util-toc/releases

[license]: LICENSE

[author]: http://barrythepenguin.github.io

[npm]: https://docs.npmjs.com/cli/install

[mdast]: https://github.com/wooorm/mdast

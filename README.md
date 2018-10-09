# SolDoc

[![NPM Package](https://img.shields.io/npm/v/@soldoc/soldoc.svg?style=flat-square)](https://www.npmjs.org/package/@soldoc/soldoc)

> A documentation generator for solidity projects, inspired by [TypeDoc](http://typedoc.org/).

## Usage

SolDoc can be used as a CLI app or as a library and called from your code.

### As a CLI tool

1. Install: `yarn global add @soldoc/soldoc` / `npm i -g @soldoc/soldoc`.
2. Use the CLI:
    ```
    Usage: cli.js --in <input dir> -o <out dir>

    Options:
    --help          Show help                                            [boolean]
    --version       Show version number                                  [boolean]
    --options       Path to JSON config file
    --in            Specifies the location the input files should be read from.
                                                [string] [default: "./contracts"]
    --json, -j      Output the parsed information to a json file instead of
                    rendering.                                            [string]
    --out, -o       Specifies the location the documentation should be written to. [string] [default: "./docs"]
    --quiet, -q     No stdout output                    [boolean] [default: false]
    --theme, -t     Specifies a npm module that exports a default
                    `render(filepath,contractName,contactInfo,options):
                    {content,extension}` function
                                            [string] [default: "@hubiinetwork/markdown"]
    --repo-url, -r  Specifies remote repository url. Uses `repository` field in
                    `package.json` if available and not specified.        [string]
    --log, -l       Specifies the location the log file should be written to.
                                                                            [string]

    Examples:
    cli.js --in ./contracts -o ./docs  Render `.sol` files in `./contracts` into
                                        `.docs`

    For more information, visit https://github.com/dev-matan-tsuberi/soldoc
    ```

### As a library

1. Install: `yarn add --dev @soldoc/soldoc` / `npm i --save-dev @soldoc/soldoc`.
2. Import in your project as:
    ```JavaScript
    import soldoc from '@soldoc/soldoc';

    /* default options */
    soldoc.defaults = {
        in: './contracts',
        out: './docs',
        /* json: undefined, */
        /* repoUrl: undefined, */
        /* log: undefined, */
        quiet: false,
        theme: '@hubiinetwork/markdown',
    };
    soldoc(options); // returns a promise
    ```

## Themes

SolDoc is easily themeable, installing a theme is as simple as `yarn add @soldoc/<theme>` / `npm i --save @soldoc/<theme>` and setting a configuration option:
1. In the cli: `soldoc --theme @soldoc/<theme>`.
2. In code: `soldoc({theme: '@soldoc/<theme>'})`.

Currently the official themes are:
1. [![NPM Package](https://img.shields.io/npm/v/@hubiinetwork/markdown.svg?style=flat-square)](https://www.npmjs.org/package/@hubiinetwork/markdown) [@hubiinetwork/markdown](packages/markdown) **\*Default\*** - A simple markdown theme.
2. [![NPM Package](https://img.shields.io/npm/v/@soldoc/json.svg?style=flat-square)](https://www.npmjs.org/package/@soldoc/json) [@soldoc/json](packages/json)  - A theme that just outputs a JSON object.
2. [Create a theme!](docs/create_a_theme.md)

You can pass custom options to `<theme>` under it's name, example:

options.json
```
{
    ...
    "theme": "@hubiinetwork/markdown",
    "@hubiinetwork/markdown": {
       ...
    }
}
```

## Contribute

Get started:

1. `git clone git@github.com:dev-matan-tsuberi/soldoc.git && cd soldoc`
2. `yarn`
3. `yarn lerna bootstrap`
4. Done.

**Note**: This project is managed as a **monorepo** and uses [lerna.js](https://lernajs.io/).

This project needs contributors!
Pull requests are very welcome and needed.
Check out [issues with label `help wanted`](https://github.com/dev-matan-tsuberi/soldoc/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22) to get started.

# Doxity

### Documentation Generator for Solidity

Uses [gatsby](https://github.com/gatsbyjs/gatsby) to generate beautiful Solidity docs automatically via [natspec](https://github.com/ethereum/wiki/wiki/Ethereum-Natural-Specification-Format).

## Installation

You can install `@digix/doxity` globally or locally in your project.

```bash
# globally
npm install -g @digix/doxity
# project folder
npm install --save-dev @digix/doxity
```

You can then use `npm run docs:[command]` as a proxy for `doxity [command]`.

## Usage

The `doxity` cli tool is designed for npm/solidity projects. It's designed for use with [Truffle](https://github.com/ConsenSys/truffle).

Here's an outline of the available commands:

* `doxity init`
  * Creates a `./scripts/doxity` directory
  * Clones [this repo](https://github.com/DigixGlobal/doxity-gatsby-starter-project.git) into it
  * Runs `npm install` in the doxity directory
  * [TODO] Set up config, copy other project details
* `doxity compile`
  * Generates Solidity devdocs, userdocs, abi, etc. using `solc`
  * Formats data and copies output into gatsby project
  * [TODO] Copies `README.md` into gatsby projec
* `doxity develop`
  * Runs `gatsby develop` start dev server on 8000 - you can then edit files the doxity (gatsby) project
* `doxity publish`
  * Runs `gatsby build` to generate the static HTML
  * Outputs to `./docs`

Unless you override them, default arguments will be used:

* `doxity init`
  * `--source` git url for bootstrappign - defaults to `https://github.com/DigixGlobal/doxity-gatsby-starter-project.git`
  * `--target` doxity source files directory - defaults to `./scripts/doxity`
* `doxity build`
  * `--target` doxity source files directory - defaults to `./scripts/doxity`
  * `--src` folder that contains the contracts you want to compile - defaults to `contracts`
  * `--dir` folder in gatsby project to dump generated docs data - defaults to `pages/docs`
* `doxity develop`
  * `--target` doxity source files directory - defaults to `./scripts/doxity`
* `doxity publish`
  * `--target` doxity source files directory - defaults to `./scripts/doxity`
  * `--out` folder to output the generated html (relative to project root) - defaults to `docs`

If you are installing locally, you could add the following to your `package.json`:

```javascript
"scripts" : {
  "docs:init": "node_modules/.bin/doxity init", // add your custom arguments (see API below)
  "docs:build": "node_modules/.bin/doxity build",
  "docs:develop": "node_modules/.bin/doxity develop",
  "docs:publish": "node_modules/.bin/doxity publish",
  "docs:compile": "npm run docs:build; npm run docs:publish", // build + publish
  ...
},
```


## Tests

`npm run test`

## License

MIT 2016
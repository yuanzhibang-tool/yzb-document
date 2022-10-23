!> Extension is a `node` package based on the `node` framework to extend the application capabilities of the open platform. Apezhibang extension complies with the following specifications

### 1. Extensions are published using `zip` archives

> The root directory of the `zip` file is the application root directory

### 2. The expansion entry is unified as `index.js`

> Ape's Stick will automatically execute `index.js` after the user calls the extension, without `index.js` it will not be able to execute

### 3. Extended runtime dependencies `node_modules` should be fully installed

> If your project depends on third-party packages, the lack of these packages will cause the extension to fail to run

### 4. Extensions should at least depend on <a href="https://www.npmjs.com/package/@yuanzhibang/node" target="_blank">@yuanzhibang/node</a> to complete life Send periodic events to improve development efficiency

> Extensions must implement several lifecycle methods to synchronize rendering to extension services.

### 5. Extensions must send lifecycle messages according to the following conventions

![Lifecycle message](../images/20220718185810.jpg ':size=500')

### 6. Do not obtain the user's privacy and other private information without instructions

!> Please programmers pay attention to their own business, do not obtain unnecessary information

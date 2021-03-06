# node-CocProxy [![Build Status](https://travis-ci.org/azu/node-cocproxy.svg)](https://travis-ci.org/azu/node-cocproxy)

Convention over Configuration Proxy written in Node.js.

- [CocProxy – CodeRepos::Share – Trac](http://coderepos.org/share/wiki/CocProxy "CocProxy – CodeRepos::Share – Trac") Ruby
- [cocproxy for nginx](https://gist.github.com/hotchpotch/990354 "cocproxy for nginx") Nginx

If you access `http://localhost:8087/http://example.com/script.js`, then the proxy get following:


1. if found `<Current Directory>/example.com/script.js` 
    - access to `<Current Directory>/example.com/script.js`
2. if not found
    - access to `http://example.com/script.js`


## Installation

```
npm install -g cocproxy
```

## Usage

## Command Line

```
$ cocproxy [options]

Options:
  -h, --help         Show help.
  -v, --version      Outputs the version number.
  -d, --mock-file-dir path::String  Set mock file from this directory
  -p, --port Number  Set port number to thi proxy
```

1. run `$ cocproxy -p 8098`
2. set proxy url for browser
    - localhost:8098
3. Access  http://example.com/example.css
    - if found `<WORKING_ROOT>/example.com/example.css`, then return this local file.
    - if couldn't found, then return http://example.com/example.css

## Node API

`cocproxy.js`

```js
var CocProxy = require("cocproxy").CocProxy;
var options = {
    port : 8087,
    mockFileDir : "./"
}
var cocProxy = new CocProxy(options);
cocProxy.start();
// proxing
cocProxy.exit();
```


## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

MIT
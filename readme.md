# config

A deno module that helps you load configuration.

## Usage

```ts
import { Config } from "https://raw.githubusercontent.com/eankeen/config/master/mod.ts"

Config.load({
  file: 'fileName'
})

// example including defaults
Config.load({
  file: 'fileName'
  searchDir: Deno.cwd()
  includeDefault: false
})
```

### Options

- `file` the name of your file
- `searchDir` the directory to start searching. this is the directory that might include a `.config` file
- `includeDefault`, if loading a js/ts module, this determines if you want an object returned that includes the `default` property (might be deprecatead soon)

### Priority

The ordering is as follows. Modules are loaded from `.config` folder first, then the parent to that folder. Rc files in `.config` never start with a dot.

- `.config/file.config.ts`
- `.config/file.config.js`
- `.config/file.toml`
- `.config/file.json`
- `.config/file.yaml`
- `.config/file.yml`
- `file.config.ts`
- `file.config.js`
- `.file.toml`
- `.file.json`
- `.file.yaml`
- `.file.yml`

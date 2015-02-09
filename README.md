# ls-deps

A utility for displaying the dependency graph of modules in your project. It's like `npm ls`, but for client-side projects based on SystemJS or StealJS.

## Usage

```shell
> ls-deps --help

Get all dependencies of a project

Examples:
  ls-deps --config config app/app    Use config to get the dependencies for app/app


Options:
  --config    A module used to configure the loader           
  --base-url  The root folder used to load modules from       
  --depth     The depth of modules to show                      [default: 3]
  --inverse   Show all of the modules that are dependants on N
  --steal     A Steal based project                           
  --version   Show version number                             

Must provide a module to fetch dependencies for
```

## Example

```shell
> ls-deps main

├─┬ foo
| ├── bar
| └─┬ baz
| | └── qux
└── bar
```

In the above example `main` is the main module and the dependencies listed are all chidren.  Use `--depth` to control how deep we go; by default we go 3 levels deep.

## Options

### --config

Specifies a module that will act as configuration for the main module you'll load. If you use [jspm](http://jspm.io/) this is most likely the `config.js` file in your root folder.

### --base-url

Specifies a folder to act as the root folder for your project. It is equivalent to `System.baseURL`.

### --depth

Specifies how *deep* to go in showing a module's dependencies. By default `ls-deps` uses a depth of **3**, which means we'll show your module's dependencies and its dependencies.

### --inverse

Inverse is a nice feature when you're trying find out what modules depend on a certain other module. To follow our example above, what if you wanted to know which modules depend on **bar**. By specifying the `inverse` option you can see all of bars dependants.

```shell
> ls-deps --inverse bar main

├─ foo
└─ qux
```

As shown above **foo** and **qux** depend on **bar**.  I use this feature to see if my coworkers are requiring all of lodash instead of the individual module they need.

### --steal

Specifies whether this project needs [StealJS](http://stealjs.com/) to load. If you use Steal in your project and you depend on Steal's special extensions, use this option. It is a boolean option, no value is needed.

## License

MIT

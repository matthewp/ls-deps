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

## License

MIT

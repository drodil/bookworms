# Advanced usage

The top level [README](../README.md) shows the basic `get` functionality but there are more options and ways to use Bookworms.

## Get

Create bookmarks from local or remote `YMAL`.

```BASH
$ npx bookworms get ./my-bookmarks.yaml
```

This will then generate in the `./` directory the different exports you can then use in your older tools.

```BASH
$ ls
browsers.html README.md
```

You can also fetch bookmarks from a remote location and output the exports into a directory:

```BASH
$ npx bookworms get https://raw.githubusercontent.com/thearegee/bookworms/main/demo/config/bookmarks.yaml -d="./output"
```

## Merge

`merge` works in a similar way to `get` with the same options but it allows you to create bookmarks from multiple local or remote `YAML`.

```BASH
$ npx bookworms merge ./my-bookmarks.yaml ./my-company-bookmarks.yaml https://raw.githubusercontent.com/thearegee/bookworms/main/demo/config/bookmarks.yaml
```

In this example Bookworms is merging together multiple bookmark `YAML` files, by default it will merge them into one top level folder called "Merged worms" but you can override the label and the description with the command:

```BASH
$ npm start -- merge ./my-bookmarks.yaml ./my-company-bookmarks.yaml https://raw.githubusercontent.com/thearegee/bookworms/main/demo/config/bookmarks.yaml -l="My bookmarks" -t="Bookmarks my personal bookmarks, my bookmarks from work and remote bookmarks that interest me"
```

## Convert

If you already have bookmarks in your browser you can speed up the process of converting them into `YAML` using the `convert` tool, read more about that here:
[Exporting existing bookmarks](./docs/EXPORTING-EXISTING-BOOKMARKS.md).

The `convert` command works in a similar way to `get` with the same options.

```BASH
$ npx convert ./browsers.html -d="./output"
```

```BASH
$ ls
converted-bookmarks.yaml
```

You can also override the default filname.

```BASH
$ npx convert ./browsers.html -f="./my-bookmarks.yaml"
```

```BASH
$ ls
my-bookmarks.yaml
```

## Check

Check whether current generated files are up to date with the yaml file.
This can be used either in a git hook or in your CI to make sure the output files have been changed after a change to the yaml file.

The `check` command works in a similar way to `get` with the same options.

```BASH
$ npx bookworms check ./my-bookmarks.yaml
```

This will print whether the generated bookmark files are up to date.
The process will also exit with exit code 0 if the files are up to date, and 1 if not.

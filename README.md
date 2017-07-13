# multishellcheck

This script is a wrapper for [ShellCheck](http://www.shellcheck.net/) to work around its [lack of support for multi-file scripts](https://github.com/koalaman/shellcheck/issues/913). 

It works by:

1. reading the supplied shell script (and, recursively, the shell scripts it sources);
2. placing the result into a single temporary file;
3. invoking `shellcheck` on that file;
4. reading `shellcheck`'s output;
5. substituting the file names and line numbers in `shellcheck`'s output with the real file names and line numbers;
6. printing the thus edited results.

## Usage

```
$ multishellcheck MAIN-FILE-NAME [SHELLCHECK-OPTIONS...]
```

If you wish to get colour output, you can enable it with the `-Calways` ShellCheck option.

## In Action

`multishellcheck` is used as part of automatic CI for `aconfmgr`, [a configuration manager for Arch Linux](https://github.com/CyberShadow/aconfmgr) written 100% in Bash.

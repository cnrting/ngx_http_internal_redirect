# ngx_http_internal_redirect_module

## Introduction

This module is used to make an internal redirect to the uri specified
according to the condition specified.

## Synopsis

```nginx
    location / {
        ...
        internal_redirect_if ($request_method == 'FOO') @foo;
        internal_redirect_if ($request_method == 'BAR') /foo;
    }

    location @foo {
        ...
    }

    location /bar {
        ...
    }
```

## Directives

* **syntax**: ***internal_redirect_if** (condition) uri*
* **default**: --
* **context**: http, server, location

The specified `condition` is evaluated. If true, an internal redirect would be made to the `uri` specified in this directive. The syntax of condition is the same as it in the `if` directive in `rewrite` module.

* **syntax**: ***internal_redirect_if_no_postponed**  on|off*
* **default**: off
* **context**: http

Control whether or not to disable postpone the `internal_redirect_if` directives to run at the end of the `REWRITE` request-processing phase. By default, this directive is turned off.

## Installation

```shell
    cd nginx-**version**
    ./configure --add-module=/path/to/this/directory
    make
    make install
```

## Status

This module is compatible with following nginx releases:
- 1.2.6
- 1.2.7

Others are not tested.

## Author

FengGu <flygoast@126.com>

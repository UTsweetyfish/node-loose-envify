# loose-envify - replace Node.js environment variables with plain strings

## SYNOPSIS
loose-envify <javascript_source_file.js>

## DESCRIPTION
Performs a Javascript source-to-source transformation (transpiling), that efficiently replaces Node.js process.env environment variables with plain strings. This makes the environment variable checks faster and easier to optimize out.

## EXAMPLES
Running this source code:
```
if (process.env.NODE_ENV === "development") {
  console.log('development only')
}
```
through loose-envify:
```
loose-envify index.js > bundle.js
```
with NODE_ENV set to production results in:
```
if ("production" === "development") {
  console.log('development only')
}
```
which, when run through a minifier, would be stripped out completely.

However, if you run the same script through loose-envify with NODE_ENV set to development it gives:
```
if ("development" === "development") {
  console.log('development only')
}
```
The if statement will evaluate to true, so the code won't be removed.

## AUTHOR
Andres Suarez `<zertosh@gmail.com>`

## COPYRIGHT
This manual page was written by Paolo Greppi `<paolo.greppi@libpf.com>` for the Debian project (and may be used by others), also based on material from the envify README (https://github.com/hughsk/envify) by Hugh Kennedy `<hughskennedy@gmail.com>` and the envify contributors.

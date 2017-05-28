# docker-alpine-zulu

## About

Based on `frolvlad/alpine-glibc:alpine-3.6`, adds Azul Systems'
[Zulu](https://www.azul.com/products/zulu/) J(DK|RE), version (7|8).

## Motive

Existing efforts to provide certified OpenJDK builds in a Docker image based on
Alpine Linux have overwhelmingly focused on Oracle's JDK, which, as far as I'm
aware, is impossible to distribute in a Docker image without violating the
terms of Oracle's license.

## Tags

* `zre-7` &mdash; JRE 7
* `zulu-7` &mdash; JDK 7
* `zre-8` &mdash; JRE 8
* `zulu-8` &mdash; JDK 8

There is no `latest` tag. Whether to base your image on a (smaller) JRE image
or one with a full JDK is a decision that should be made on a per-Dockerfile
basis. In an ideal world, a full JDK would never be required for deployment,
but sometimes it's required for compiling JSPs, etc.

## Details

`JAVA_HOME` is `/opt/zulu`. This variable is set from the Dockerfile and
`/etc/profile.d/zulu.sh`, along with adding `$JAVA_HOME/bin` to `PATH`.

## License

This repository is made available under the terms of the MIT license. See
`LICENSE` for details.

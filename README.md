# bips-hb.r-universe.dev

This contains the index for the [r-universe repository](https://bips-hb.r-universe.dev/builds).

The R-universe project provides an alternative package repository ecosystem including automated package builds and checks outside of the familiar CRAN or BioConductor infrastructure.

Aside from the discoverability bonus (see e.g. the [R-universe landing page](https://r-universe.dev/)), the additional build system also allows package installation via `install.packages()`:

You can continue to install e.g. the CRAN version of [arf](https://github.com/bips-hb/arf) like this:

```r
install.packages("arf"z)
```

Or you can install the current development version from GitHub and built by R-universe like this:

```r
install.packages("arf", repos = "https://bips-hb.r-universe.dev")
```

Note that

1. You do not need to use `remotes::instal_github()` or similar solutions
2. This will install a binary package that does not require compilation on Windows, macOS, and as of [November '23, also WASM binaries](https://ropensci.org/blog/2023/11/17/runiverse-wasm/).

The WASM binaries are for use with [webR](https://docs.r-wasm.org/webr/latest/) to run R in the browser.

## Enable it globally

You can also choose to always draw from this repository when using `install.packages()` by adding its URL to your `repos` option like this (e.g. in your `~/.Rprofile`):

```r
options(repos = c(
  "bips-hb" = "https://bips-hb.r-universe.dev",
  CRAN = "https://cloud.r-project.org/"
))
```

The next time you try to install one of the packages available at the BIPS R-universe, this repository will now be preferred over the CRAN repository.
That means that you can install a binary (on Windows and macOS) version of the latest GitHub version of each package the same way you would normally install CRAN packages:

```r
install.packages("arf")
```

**Please be warned** however that if you explicitly want to install the latest CRAN release, you will need to specify this accordingly, i.e. by using

```r
install.packages("arf", repos = "https://cloud.r-project.org/")
```

...which is why it may not be desirable to add the repository to your global `repos`.

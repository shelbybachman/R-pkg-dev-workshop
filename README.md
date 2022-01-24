# R package development workshop

notes from the R Package Development Workshop from R-Ladies Remote

## part 1: packages in a nutshell

source: [slides from R-Ladies Remote](bit.ly/pkg-dev-1)

### where are packages located on my machine?

-   see default R library: enter `.Library` in R command window
-   you may or may not have write access to the default library
-   see additional libraries that R knows about: `.libPaths()`

### where do R packages come from?

-   CRAN (`install.packages('pkg_name')`)
-   GitHub (`remotes::install_github('repo_name/pkg_name')`)
-   Bioconductor (`BiocManager::install('celaref')`)

### info on installed packages

-   number of installed packages: number of rows in `dim(installed.packages())`

### startup files

-   `.Rprofile`: contains code that runs at startup (loads workflow packages, sets options, etc.)
-   `.Renviron`: contains settings for(sets library paths and environment variables, etc.)

### scripts vs. packages

-   **scripts**:

    -   used for one-off purpose
    -   defined by `.R` file extension
    -   required packages loaded with `library()`
    -   documentation in comments
    -   to use, call with `source()`

-   **packages**:

    -   defines reusable components
    -   defined by `DESCRIPTION` file
    -   required packages made in `NAMESPACE` file
    -   documentation in separate files and `Roxygen` comments
    -   to use, install package and restart R

### package states

-   a package can be in 5 states: source, bundled, binary, installed, in-memory

    -   *bundle*: also known as a "source tarball", a single file that gets submitted to CRAN
    -   *binary*: also a single file, gets built by CRAN

-   `install.packages()` (via CRAN) by default installs the binary

    -   option to install from source will install the bundle vs. binary, but takes longer due to compilation of source code

-   `R CMD install`, which can be called from the command line, can take either a bundle or binary and install it

-   `devtools` package provides several functions:

    -   `install()` installs the source
    -   `build()` compiles the source to a bundle
    -   `install_github()` downloads the source from github and builds it

-   if a package is installed, `library()` makes its functions available by loading into memory

-   when developing, instead of using `library()`, we will use `devtools::load_all()` to load a source package directly into memory for interactive stepping-through package R code


## part 2: setting up your system

source: [slides from R-Ladies Remote](bit.ly/pkg-dev-1)

### devtools

- makes package development easier by providing R functions that simplify and expedite common tasks
- installs source packages from Github/elsewhre
- installs and develops packages that you like

### check that your system is ready for package development

- install Xcode (if on mac)
- install `devtools` and run `devtools::has_devel()`
- install git

# Provider perspective: Secure build

## Internal build

- Prepare an internal container, compliant with IT security standards
  - secure configuration of container running system (base system)
  - add layer of common software (Stata, R, Python, various combinations) for **analysis system**
  - test suite (scripted) for updates
- Can leverage existing container recipes for well-known software packages (`rocker` for R containers, datascience containers)
- Can leverage existing containers and harden the OS (if necessary)


## Public build

- Public "recipe" is the same as for internal
  - possibly up to secure base container - close enough is good enough
  - built by StatAgency itself

## Example: Build internal analysis system

```Dockerfile
FROM registry.internal.statagency.gov/os/ubuntu-24.04-secured

# Install Stata from internal sources (simple tar file), no license
...
# Install R from internal sources
...
USER rstudio
```

## Example: Build public analysis system

```Dockerfile
FROM ubuntu-24.04

# Install Stata from internal sources (simple tar file), no license
...
# Install R from internal sources
...
USER rstudio
```

## Optional elements

While not strictly necessary, containers might contain

- development environments (Stata GUI, Jupyter notebooks, Rstudio)
- standard set of libraries (Stata ado files, R libraries, Python packages)

## Necessary restrictions

While useful in the public space, when running internally and for pre-vetting,

- containers would be restricted in terms of internet access
- containers may be built against only known safe sources of packages

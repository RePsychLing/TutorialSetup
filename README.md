---
title : Tutorial Setup
author: Phillip Alday, Douglas Bates, Reinhold Kliegl
date  : February 17-19, 2020
---

A tutorial on *Mixed Models in the Julia Programming Language* will be held February 17-19, 2020 at the Zentrum fur interdisziplinare Forschung (ZiF) at the University of Bielefeld. In preparation for this tutorial, please follow these instructions to install Julia on the computer you will be using.

We assume that those participating in the tutorial are somewhat familiar with [`R`](https://R-project.org) and the [`RStudio`](https://rstudio.com/products/rstudio) IDE (integrated development environment).

## Installing Julia

The [Julia download site](https://julialang.org/downloads/) provides binary downloads for most common operating systems. Ensure that the version you install is at least v1.3.0. By the time of the tutorial v1.4.0 may have been released - if so please install that version.

## The Julia REPL

By itself the Julia binary provides a basic REPL (read-eval-print-loop), which is quite adequate for installing packages. (Installing and using IDE's for Julia is discussed below.) When you start Julia you are in julia mode, as indicated by the `julia> ` prompt.

Typing certain characters as the first in an input line will change the mode of the REPL.

| Character | Prompt | Context |
| --------- | ------ | --------------- |
| `?` | `help?> ` | Help mode - print help messages on functions, types, etc. |
| `]` | `(v1.3) pkg> ` | Pkg mode - install, list, remove, etc. packages |
| `;` | `shell> ` | Shell mode - execute a single shell command |
| `$` | `R> ` | R mode - requires `RCall` package installed and active |
| `<backspace>` | `julia> ` | return to Julia mode |

## Julia packages

### The Standard Library

A binary installation of Julia includes several packages in the standard library. They are listed and documented as part of the general documentation at https://docs.julialang.org. Most of the time a user does not need to be conscious of these packages but occasionally we will attach one explicitly.

For example
~~~~{.julia}
julia> using InteractiveUtils, Random, Statistics

julia> varinfo(Random)   # list exported functions and types
  name                   size summary            
  ––––––––––––––– ––––––––––– –––––––––––––––––––
  AbstractRNG       176 bytes DataType           
  MersenneTwister   232 bytes DataType           
  Random          525.723 KiB Module             
  RandomDevice      200 bytes DataType           
  bitrand             0 bytes typeof(bitrand)    
  rand!               0 bytes typeof(rand!)      
  randcycle           0 bytes typeof(randcycle)  
  randcycle!          0 bytes typeof(randcycle!) 
  randexp             0 bytes typeof(randexp)    
  randexp!            0 bytes typeof(randexp!)   
  randn!              0 bytes typeof(randn!)     
  randperm            0 bytes typeof(randperm)   
  randperm!           0 bytes typeof(randperm!)  
  randstring          0 bytes typeof(randstring) 
  randsubseq          0 bytes typeof(randsubseq) 
  randsubseq!         0 bytes typeof(randsubseq!)
  shuffle             0 bytes typeof(shuffle)    
  shuffle!            0 bytes typeof(shuffle!)   

julia> varinfo(Statistics)
  name              size summary                     
  –––––––––– ––––––––––– ––––––––––––––––––––––––––––
  Statistics 250.283 KiB Module                      
  cor            0 bytes typeof(Statistics.cor)      
  cov            0 bytes typeof(Statistics.cov)      
  mean           0 bytes typeof(Statistics.mean)     
  mean!          0 bytes typeof(Statistics.mean!)    
  median         0 bytes typeof(Statistics.median)   
  median!        0 bytes typeof(Statistics.median!)  
  middle         0 bytes typeof(Statistics.middle)   
  quantile       0 bytes typeof(Statistics.quantile) 
  quantile!      0 bytes typeof(Statistics.quantile!)
  std            0 bytes typeof(Statistics.std)      
  stdm           0 bytes typeof(Statistics.stdm)     
  var            0 bytes typeof(Statistics.var)      
  varm           0 bytes typeof(Statistics.varm)     

~~~~~~~~~~~~~





### User-contributed Packages

A listing of registered Julia packages is available at https://pkg.julialang.org/.  Note the panel on the left where you can search by name or filter by tags on the packages.  Packages we will use include

| Name | Purpose |
| ---- | ----------- |
| CSV | read and write comma-separated-value files |
| CategoricalArrays | `factor`-like objects |
| DataFrames | data tables with properties and capabilities like R's `data.frame` |
| DataFramesMeta | database-like operations on data tables |
| MixedModels | fit and examine mixed-effects models |
| PooledArrays | light-weight version of categorical arrays |
| RCall | call R from Julia, including data transfers |
| RData | read data tables stored in `.rda` or `.rds` format |
| Tables | general data table structures - either row- or column-oriented |
| Weave | similar to the `knitr` package for R |

These packages must be added (similar to `package.install` in R) before they can be attached with `using` (similar to `library` or `require` in R).  In the package REPL (accessed by typing `]` as the first character of a line) just type `add Tables`, for example.  Note that you must have R installed on your computer to be able to successfully install the `RCall` package in Julia.

This document was created from the file `README.jmd` in this repository using `Weave` as
~~~~{.julia}

using Weave
weave("README.jmd", doctype="pandoc")
~~~~~~~~~~~~~




## Integrated Development Environments

Editing and running Julia code is supported in both the [Atom editor](https://atom.io) and [VSCode](https://code.visualstudio.com).  The Atom support is called Juno and is documented at https://junolab.github.io.  The VSCode support is documented at https://www.julia-vscode.org

Either of these environments is fine for this workshop.

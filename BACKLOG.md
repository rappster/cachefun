# cachefun 0.1.0

* `BLI-1`: carefully think about default setting of `refresh`. 

  Really depends on the most frequent use case: avoid unnecessary re-executions of long-running functions (probably mostly linked to data I/O and data wrangling) or avoid confusion through forgetting to refresh cached results.
  
  It's probably best to go with `refresh = TRUE` here.
  
* `BLI-2`: is context information via `.verbose` really that relevant? 

  Adds clarity, but hurts performance and I don't like the current implementation of `.verbose` in the  `shiny::reactive`.
  
* `BLI-3`: find out what would be best practice regarding setting defaults arg values in inner function returned by `caf_create` 

* `BLI-4`: understand **where** the cached information is actually stored and how it can be purged (to allow explicit purges/removals like via `rm`)

# cachefun 0.1.1

* `BLI-5`: should `...` that is passed to inner function be moved to the front of formal arguments of `caf_create`? Would allow for a more natural usage experience and probably also required for compatibility with the tidyverse/piping paradigm 

* `BLI-6`: implement features that allow ones function's cache to observe the cache of another functions (i.e. classical shiny observer/reactive scenario including invalidation, etc.)

* `BLI-7`: do we need some options for strictness? E.g. return warning or error if cache is still empty but `refesh = FALSE`? Think about this a bit more before going ahead with any implementation

# cachefun 0.1.2

* `BLI-8`: there are probably better ways to implement observable dependencies (see arg `observes` in `caf_create`). Check shiny internals and/or ask for help from community

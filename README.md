# ARM-rstudio-server
Build script for rstudio-server on an Raspberry Pi 3B+

Forked and tweaked from [jrowen/ARM-rstudio-server](https://github.com/jrowen/ARM-rstudio-server), which was built on the excellent work of [dashaub/ARM-RStudio](https://github.com/dashaub/ARM-RStudio).

# Notes for Success

* You probably have to increase your swap file size to get this to work. I used a variable swap up to 16GB.
* The `VERS` variable in the script can be updated to build different versions of the server.  The latest version number and be found on the rstudio server [download page](https://www.rstudio.com/products/rstudio/download-server/), and note that this will likely differ from the latest desktop version.
* This is gonna take a looooong time. Seriously. Grab some popcorn.



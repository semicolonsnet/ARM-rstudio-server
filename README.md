# ARM-rstudio-server
Build script for rstudio-server on an Raspberry Pi 4B.

Forked and tweaked from [jrowen/ARM-rstudio-server](https://github.com/jrowen/ARM-rstudio-server), which was built on the excellent work of [dashaub/ARM-RStudio](https://github.com/dashaub/ARM-RStudio).

# Notes for Success

* Optimized for Raspbian Buster and rPi4. Not sure how this will work on other versions.
* You probably have to increase your swap file size to get this to work. I used a variable swap up to 16GB.
* The `VERS` variable in the script can be updated to build different versions of the server.  The latest version number and be found on the rstudio server [download page](https://www.rstudio.com/products/rstudio/download-server/), and note that this will likely differ from the latest desktop version.
* Make sure only openjdk-8 is installed. As far as I know, this produces errors with all other versions. If anyone knows how to specify which version is used for compile, please let me know.
* This is gonna take a looooong time (roughly 50 hours on my setup). Grab some popcorn.

# Benchmarks

Results of [R-benchmark-25](https://mac.r-project.org/benchmarks/) on Raspberry Pi 4B w 4 GB RAM running Raspbian Stretch (R 3.5.2 , RStudio 1.2.1335):

     R Benchmark 2.5.  
      ===============. 
      Number of times each test is run__________________________:  3. 
      
         I. Matrix calculation
         ---------------------
      Creation, transp., deformation of a 2500x2500 matrix (sec):  2.40233333333329   
      2400x2400 normal distributed random matrix ^1000____ (sec):  1.23333333333335   
      Sorting of 7,000,000 random values__________________ (sec):  1.8253333333333  
      2800x2800 cross-product matrix (b = a' * a)_________ (sec):  24.9799999999999   
      Linear regr. over a 3000x3000 matrix (c = a \ b')___ (sec):  12.2486666666667  
                            --------------------------------------------
                       Trimmed geom. mean (2 extremes eliminated):  3.7730111562935   
          
         II. Matrix functions  
         --------------------
      FFT over 2,400,000 random values____________________ (sec):  1.58200000000003   
      Eigenvalues of a 640x640 random matrix______________ (sec):  2.59399999999997   
      Determinant of a 2500x2500 random matrix____________ (sec):  13.0206666666667   
      Cholesky decomposition of a 3000x3000 matrix________ (sec):  11.0676666666666   
      Inverse of a 1600x1600 random matrix________________ (sec):  10.2283333333333   
                            --------------------------------------------  
                      Trimmed geom. mean (2 extremes eliminated):  6.64676470591846   
          
         III. Programmation    
         ------------------
      3,500,000 Fibonacci numbers calculation (vector calc)(sec):  1.51333333333325   
      Creation of a 3000x3000 Hilbert matrix (matrix calc) (sec):  1.05500000000006   
      Grand common divisors of 400,000 pairs (recursion)__ (sec):  1.22166666666665   
      Creation of a 500x500 Toeplitz matrix (loops)_______ (sec):  0.204333333333276   
      Escoufier's method on a 45x45 matrix (mixed)________ (sec):  1.08300000000008   
                            --------------------------------------------  
                      Trimmed geom. mean (2 extremes eliminated):  1.11757809329357   
      
        
      Total time for all 15 tests_________________________ (sec):  86.2596666666665   
      Overall mean (sum of I, II and III trimmed means/3)_ (sec):  3.03756391468908   
                           --- End of test ---  

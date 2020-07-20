## Below are the pair of functions that creates a special matrix and then stores
## caches the inverse of the matrix
## makeCacheMatrix is a function that returns a list od functions 

makeCacheMatrix <- function(x = matrix()) {
         z <- NULL
         set <- function(y) {
                 x <<- NULL
         }
         get <- function() x
         setInverse <- function(inverse) z <<- inverse
         getInverse <- function() z
         list(set = set,
              get = get,
              setInverse = setInverse,
              getInverse = getInverse)
}              


## This function computes the inverse of the "matrix" which is created from makecacheMatrix.
## Then we can retrieve the inverse from cache
## CacheSolve- Return a matrix that is the inverse of 'x'

cacheSolve <- function(x,...) {
        ## Return a matrix that is the inverse of 'x'
        i <- x$getInverse()
        if(!is.null(i)) {
                 message("getting cache data")
                 return (i)
        }
        mat <- x$get()
        i <- solve(mat,...)
        x$setInverse(i)
        i
}        

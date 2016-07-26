From book Advanced R - Hadley Wickham

Exercises - Functions

What function allows you to tell if an object is a function? What function allows you to tell if a function is a primitive function?
function(name)
is.primitive(name)

This code makes a list of all functions in the base package.

objs <- mget(ls("package:base"), inherits = TRUE)
funs <- Filter(is.function, objs)
Use it to answer the following questions:

Which base function has the most arguments?

> which.max(lapply(funs, function(x) length(formals(x))))
scan (with 937 arguments)

How many base functions have no arguments? What’s special about those functions?
> sum(sapply(funs, function(x) length(formals(x))==0))
225

How could you adapt the code to find all primitive functions?
> sum(sapply(funs, is.primitive))
183

What are the three important components of a function?
Body, arguments, environment

When does printing a function not show what environment it was created in?
when it was created in global environment
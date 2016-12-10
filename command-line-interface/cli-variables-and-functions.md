# Variables

## Defining variables
`variable_name=variable_value` - define variable
Example: `NAME="Zara Ali"`

## Accessing values
`$variable_name` - to access the value stored in a variable, prefix its name with the dollar sign ( $)
Example: `echo $NAME`

## Unsetting variables
`unset variable_name` - remove the variable from the list of variables that shell tracks

# Functions

## Creating functions
```
function_name () { 
   list of commands
}
```
Example:
```
# Define your function here
Hello () {
   echo "Hello World"
}
# Invoke your function
Hello
```

## Unsetting functions
`unset .f function_name` - the same command you use to remove the definition of a variable to the shell, but with `.f` option
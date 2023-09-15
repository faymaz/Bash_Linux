# Bash_Linux


## Other Special Variables
```
There are a few other variables that the system sets for you to use as well.
$0 - The name of the Bash script.
$1 - $9 - The first 9 arguments to the Bash script. (As mentioned above.)
$# - How many arguments were passed to the Bash script.
$@ - All the arguments supplied to the Bash script.
$? - The exit status of the most recently run process.
$$ - The process ID of the current script.
$USER - The username of the user running the script.
$HOSTNAME - The hostname of the machine the script is running on.
$SECONDS - The number of seconds since the script was started.
$RANDOM - Returns a different random number each time is it referred to.
$LINENO - Returns the current line number in the Bash script.
$HOME - /Users/faymaz
$SHELL -
$LOGNAME -
$USER -
```
env list of all local variables

## Setting Our Own Variables
```
variable=value
```
```
read user_input
# Print the entered string
echo "Welcome $user_input"
```

```
read num1
read num2

echo "$((num1 + num2))"
echo "$((num1 - num2))"
echo "$((num1 * num2))"
echo "$((num1 / num2))"
```

example
```
#!/bin/bash

# Define two integer variables
num1=5
num2=3

# Add the two integers and store the result in a third variable
result=$((num1 + num2))

# Print the result
echo "The sum of $num1 and $num2 is: $result"
```


## Basic If Statements

### Operator Description
```
! EXPRESSION 	The EXPRESSION is false.
-n STRING 	The length of STRING is greater than zero.
-z STRING 	The lengh of STRING is zero (ie it is empty).
STRING1 = STRING2 	STRING1 is equal to STRING2
STRING1 != STRING2 	STRING1 is not equal to STRING2
INTEGER1 -eq INTEGER2 	INTEGER1 is numerically equal to INTEGER2
INTEGER1 -gt INTEGER2 	INTEGER1 is numerically greater than INTEGER2
INTEGER1 -lt INTEGER2 	INTEGER1 is numerically less than INTEGER2
-d FILE 	FILE exists and is a directory.
-e FILE 	FILE exists.
-r FILE 	FILE exists and the read permission is granted.
-s FILE 	FILE exists and it's size is greater than zero (ie. it is not empty).
-w FILE 	FILE exists and the write permission is granted.
-x FILE 	FILE exists and the execute permission is granted.
-lt as opposed to -le (less than as opposed to less than or equal).
```


```
if [ <some test> ]
then
<commands>
fi
```


example
```
#!/bin/bash
# Basic if statement
if [ $1 -gt 100 ]
then
echo Hey that\'s a large number.
pwd
fi
date
```

### If Elif Else
```
if [ <some test> ]
then
<commands>
elif [ <some test> ]
then
<different commands>
else
<other commands>
fi
```
example
```
#!/bin/bash
# elif statements
if [ $1 -ge 18 ]
then
echo You may go to the party.
elif [ $2 == 'yes' ]
then
echo You may go to the party but be back before midnight.
else
echo You may not go to the party.
fi
```
## Boolean Operations
and - &&
or - ||
example

```
#!/bin/bash
# and example
if [ -r $1 ] && [ -s $1 ]
then
echo This file is useful.
fi
```
example

```
#!/bin/bash
# or example
if [ $USER == 'bob' ] || [ $USER == 'andy' ]
then
ls -alh
else
ls
fi
```

## Case Statements

```
case <variable> in
<pattern 1>)
<commands>
;;
<pattern 2>)
<other commands>
;;
esac
```
example

```
#!/bin/bash
# case example
case $1 in
start)
echo starting
;;
stop)
echo stoping
;;
restart)
echo restarting
;;
*)
echo don\'t know
;;
esac
```

example
```
    #!/bin/bash
    # Print a message about disk useage.
    space_free=$( df -h | awk '{ print $5 }' | sort -n | tail -n 1 | sed 's/%//' )
    case $space_free in
    [1-5]*)
    echo Plenty of disk space available
    ;;
    [6-7]*)
    echo There could be a problem in the near future
    ;;
    8*)
    echo Maybe we should look at clearing out old files
    ;;
    9*)
    echo We could have a serious problem on our hands soon
    ;;
    *)
    echo Something is not quite right here
    ;;
    esac
```


## For Loops
### While Loops
```
while [ <some test> ]
do
<commands>
done
```
example

while_loop.sh

    #!/bin/bash
    # Basic while loop
    counter=1
    while [ $counter -le 10 ]
    do
    echo $counter
    ((counter++))
    done
    echo All done

### Until Loops
until [ <some test> ]
do
<commands>
done



    #!/bin/bash
    # Basic until loop
    counter=1
    until [ $counter -gt 10 ]
    do
    echo $counter
    ((counter++))
    done
    echo All done




```
for var in <list>
do
<commands>
done
```

### Ranges
```
#!/bin/bash
# Basic range in for loop
for value in {1..5}
do
echo $value
done
echo All done
```

```
#!/bin/bash
# Basic for loop
names='Stan Kyle Cartman'
for name in $names
do
echo $name
done
echo All done
```


example
```
#!/bin/bash

# Define the number of odd natural numbers to generate
n=10

# Initialize a variable to keep track of the current number
current=1

# Loop to generate and print odd natural numbers
while [ $current -le $n ]; do
    # Check if the current number is odd
    if [ $((current % 2)) -ne 0 ]; then
        echo $current
    fi

    # Increment the current number
    ((current++))
done
```


```
ls /etc | wc -l
read -p 'Username: ' uservar
read -sp 'Password: ' passvar
let <arithmetic expression>
expr item1 operator item2

```
## Operator Operation
```
+, -, \*, / 	addition, subtraction, multiply, divide
var++ 	Increase the variable var by 1
var-- 	Decrease the variable var by 1
% 	Modulus (Return the remainder after division)
```
example

```
#!/bin/bash
# Basic arithmetic using double parentheses
a=$(( 4 + 5 ))
echo $a # 9
a=$((3+5))
echo $a # 8
b=$(( a + 3 ))
echo $b # 11
b=$(( $a + 4 ))
echo $b # 12
(( b++ ))
echo $b # 13
(( b += 3 ))
echo $b # 16
a=$(( 4 * 5 ))
echo $a # 20
```



## Length of a Variable
```
${#variable}
```

= is slightly different to -eq. [ 001 = 1 ] will return false as = does a string comparison (ie. character for character the same) whereas -eq does a numerical comparison meaning [ 001 -eq 1 ] will return true.

*) set -e
In bash scripting, the "set +e ” command is used to temporarily disable the exit-on-error feature. This feature, when enabled, “set -e” causes a shell script to immediately terminate if any command within it returns a non-zero exit status.

```
cat << EOF
Bla bla
bla balalalals
Check out the README file on GitHub to do 1 quick thing manually:
You can safely close this terminal.
EOF
```



Sources:
[https://ryanstutorials.net/bash-scripting-tutorial](https://ryanstutorials.net/bash-scripting-tutorial)

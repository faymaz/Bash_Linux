# Bash_Linux
```
Operator 	Description
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


## For Loops
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

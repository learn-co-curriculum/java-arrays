# Arrays

## Learning Goals

- Understand what an array is.
- Work with Java arrays.

## What is an Array?

An **array** is a special type of variable that can hold multiple variables of
the same data type. We can think of arrays any time we think of "multiples". A
classroom, for example, may have a single teacher, but it would have multiple
students. A vehicle might have a single engine, but it would have multiple
wheels. Each variable within the array is referred to as an **element** and
these elements can be of any data type that we have mentioned thus far and more
that we'll learn in later lessons. This means that an array could hold the data
types `int`, `double`, `boolean`, or `String`!

## Working with Arrays

To declare an array, we can use the following syntax:

`variableType[] arrayName`

We first state the type of variable the array will hold and follow it with `[]`
to indicate that instead of the variable holding a single value, it will hold
multiple values. We then give the array a name, like we would with any other
variable.

`String[] names` declares an array of `String` types called `names`.

An array can be initialized as follows:

`String[] names = {"Leslie", "Ann", "Ron", "Ben"};`

Once the array is initialized, each value in the array can be referenced by its
position in the array (called its **index**). In programming languages, when we
count indices, we start with 0 instead of 1. This is because we consider the
question: "How many positions would we need to move in order to get to that
value?" If the value we want is the first within the list, we say we move 0
positions. So if we want to find out the first value in the array, `names`, we
can do so by writing `names[0]`. We specify the index within the square brackets
of the position in the array we want to access: `array[index]`. In this case,
`names[0]` would evaluate to the `String` value Leslie.

`System.out.println(names[0]);` will print the name Leslie to the console while
`System.out.println(names[1]);` will print the name Ann to the console.

We can see a familiar pattern where the index of the value we want to print
increases by one every time we want to move on to the next item in the array.
This is a perfect use case for a `for` loop. Let's put one together to go
through and print every name in our array:

```java
String[] names = {"Leslie", "Ann", "Ron", "Ben"};
for (int nameIndex = 0; nameIndex < 4; nameIndex++) {
    System.out.println("Current name = " + names[nameIndex]);
}
```

This will produce the following output:

```plainttext
Current name = Leslie
Current name = Ann
Current name = Ron
Current name = Ben
```

This does the job, but we can improve the loop by basing the condition on the
length of the array instead of hardcoding it to 4. We can find the length of the
array by calling its `length` property like so: `names.length`. The `length`
property holds the number of elements in the array. By making use of this
property, the code will still work if the array has a different number of
elements in it:

```java
String[] names = {"Leslie", "Ann", "Ron"};
for (int nameIndex = 0; nameIndex < names.length; nameIndex++) {
    System.out.println("Current name = " + names[nameIndex]);
}
```

The condition is now based on `names.length`, which returns the number of
elements in the `names` array. The example code above also removed the last
element of the array ("Ben") to demonstrate that the new code now works even
though the array has one less element than it did before.

Here is the output from this code:

```plaintext
Current name = Leslie
Current name = Ann
Current name = Ron
```

Another way to go through each element in the array is to use a special version
of the `for` loop that will iterate through each element in the array:

```java
String[] names = {"Leslie", "Ann", "Ron"};
for (String name: names) {
    System.out.println("Current name = " + name);
}
```

This code produces the same output as the previous version. Java knows that
`names` is an array, and this syntax indicates that we want to go through each
item in the array and assign it temporarily to the `name` variable, which can
then be used in the loop for whatever logic we need. The code above is
equivalent to the following code:

```java
String[] names = {"Leslie", "Ann", "Ron"};
for (int nameIndex = 0; nameIndex < names.length; nameIndex++) {
    String name = names[nameIndex];
    System.out.println("Current name = " + name);
}
```

We have been initializing our sample array with actual values, but an array can
also be defined by specifying its size:

```java
int[] numbers = new int[10];
```

The `new` instruction here tells Java to create a new array of integers. We'll
learn more about the `new` keyword in the next module when we talk about objects.

Once the array is initialized, any of its elements can be referenced by their
index.

```java
numbers[0] = 7; // initializes the first item in the array
```

If the contents of the array are not initialized, it will print the default
values of the data types. Consider the table of data types and their default
values:

| Data Type                         | Default Value  |
|-----------------------------------|----------------|
| `int`, `long`, `byte`, `short`    | 0              |
| `float`, `double`                 | 0.0            |
| `boolean`                         | `false`        |
| `char`                            | '\u0000'       |
| Reference type (such as `String`) | `null`         |

By the table above, this means if we have an array of `int` data types, it will
print out the value `0` for any element that is not assigned:

![print-default-integer-array](https://curriculum-content.s3.amazonaws.com/java-mod-1/arrays/print-default-integer-array.png)

If we have an array of `double` data types, it will print out the value `0.0`
for any element that is not assigned:

![print-default-double-array](https://curriculum-content.s3.amazonaws.com/java-mod-1/arrays/print-default-double-array.png)

And if we have an array of `boolean` data types, it will print out the value
`false` for any element that is not assigned:

![print-default-boolean-array](https://curriculum-content.s3.amazonaws.com/java-mod-1/arrays/print-default-boolean-array.png)

Arrays in Java have two majors constraints:

1. Their size is fixed - once an array has been defined to be a certain size,
   its size cannot be changed.
2. All elements in an array have to be the same type. That means we cannot have
   an array with a mixture of `int` data types and `double` data types.
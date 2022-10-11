# State in Jetpack Compose

In this session, we will learn about state in Jetpack Compose. We will learn how to use state in Jetpack Compose and how to use it to build a simple tip calulating app.

## What is State?

State is a value that can change over time. In Jetpack Compose, state is represented by a `State` object. A `State` object can be mutable or immutable. Mutable `State` objects can be changed by the user. Immutable `State` objects can only be changed by the system.

## Automatic State Management

In Jetpack Compose, state is automatically managed. This means that when a state changes, the UI will automatically update to reflect the new state. This is done by using the `@Composable` annotation. The `@Composable` annotation tells the compiler that the function is a composable function. A composable function is a function that can be used to build the UI. When a composable function is called, the compiler will automatically update the UI to reflect the new state.



## mutableStateOf

mutableStateOf is a function that takes an initial value and returns a MutableState<T> object. MutableState<T> is a wrapper around a value of type T. It has a value property that can be used to read and write the value. It also has a setter function that can be used to update the value.

Let's see how to use mutableStateOf to create a MutableState<String> object.

```kotlin
val name = mutableStateOf("Android")
```

We can read the value of the MutableState<String> object using the value property.

```kotlin
val name = mutableStateOf("Android")
val nameValue = name.value
```

## remember

The `remember` function is used to create a state object. It takes a lambda as an argument and returns the value of the lambda. The lambda is only executed once and the value is cached. The value is cached in the composition. The value is recomposed when the composition is recomposed.

```kotlin
val count = remember { mutableStateOf(0) }
```

## rememberSaveable

The `rememberSaveable` function is used to create a state object that is saved when the app is killed. It takes a lambda as an argument and returns the value of the lambda. The lambda is only executed once and the value is cached. The value is cached in the composition. The value is recomposed when the composition is recomposed.

```kotlin
val count = rememberSaveable { mutableStateOf(0) }
```

## lambda functions

Lambda functions are anonymous functions that can be passed as arguments to other functions. They are also called closures. They are defined using curly braces. They can have parameters and a return type. They can be passed as arguments to other functions. They can be assigned to variables.

```kotlin
val add = { a: Int, b: Int -> a + b }
val addResult = add(1, 2)
```

## Callbacks

Callbacks are functions that are passed as arguments to other functions. They are executed when the function is executed. They are used to execute code asynchronously.

```kotlin
fun add(a: Int, b: Int, callback: (Int) -> Unit) {
    val result = a + b
    callback(result)
}

add(1, 2) { result ->
    println(result)
}
```

## State Hoisting

State hoisting in Compose is a pattern of moving state to a composable's caller to make a composable stateless. The general pattern for state hoisting in Jetpack Compose is to replace the state variable with two parameters:

- A state parameter that is passed to the composable
- A callback parameter that is used to update the state

```kotlin
@Composable
fun Counter(count: Int, updateCount: (Int) -> Unit) {
    Button(onClick = { updateCount(count + 1) }) {
        Text("I've been clicked $count times")
    }
}

@Composable
fun MyApp() {
    var count by remember { mutableStateOf(0) }
    Counter(count) { newCount ->
        count = newCount
    }
}
```

## Using Compose State as source of truth

Let's see an example using TextFields to update a state variable.

```kotlin
@Composable
fun MyApp() {
    var name by remember { mutableStateOf("") }
    Column {
        TextField(
            value = name,
            onValueChange = { name = it },
            label = { Text("Name") }
        )
        Text("Hello $name")
    }
}
```
<!-- Explaination of the code -->
In the above code, we are using a TextField to update the name state variable. The TextField has a value parameter that is used to read the value of the TextField. The TextField has an onValueChange parameter that is used to update the value of the TextField. The value of the TextField is updated when the onValueChange parameter is called.

## Building a Tip Calculator

Let's build a tip calculator app using Jetpack Compose. The app will have one TextField for the bill amound and 3 buttons for 10%, 20% and 25% tip. The app will also have a Text composable to display the tip amount.

```kotlin
@Composable
fun MyApp() {
    var billAmount by remember { mutableStateOf("") }
    var tipPercentage by remember { mutableStateOf(0.1f) }
    var tipAmount by remember { mutableStateOf(0.0f) }
    Column {
        TextField(
            value = billAmount,
            onValueChange = { billAmount = it },
            label = { Text("Bill Amount") }
        )
        Row {
            Button(onClick = { tipPercentage = 0.1f }) {
                Text("10%")
            }
            Button(onClick = { tipPercentage = 0.2f }) {
                Text("20%")
            }
            Button(onClick = { tipPercentage = 0.25f }) {
                Text("25%")
            }
        }
        Text("Tip Amount: $tipAmount")
    }
}
```

<!-- Explaination of the code -->

In the above code, we are using a TextField to update the billAmount state variable. The TextField has a value parameter that is used to read the value of the TextField. The TextField has an onValueChange parameter that is used to update the value of the TextField. The value of the TextField is updated when the onValueChange parameter is called.

We are using 3 Buttons to update the tipPercentage state variable. The Button has an onClick parameter that is used to update the value of the Button. The value of the Button is updated when the onClick parameter is called.

We are using a Text composable to display the tipAmount state variable. The Text composable has a text parameter that is used to read the value of the Text composable. The Text composable has a modifier parameter that is used to update the value of the Text composable. The value of the Text composable is updated when the modifier parameter is called.


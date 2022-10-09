# Creating UI layouts using Jetpack Compose
<!-- Copyright -->
```
[]: # (c) 2022, Vishesh Raheja @entropyconquers
```




<!-- Jetpack Compose Column desciption -->

## Column
### Y-ordered stack of children
Column is a layout that places its children in a vertical sequence. It sizes its children to their preferred height and the width of the widest child. It positions its children relative to its top edge and may optionally clip them if they extend beyond its bottom edge.

<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.fillMaxSize(),
    horizontalAlignment = Alignment.CenterHorizontally,
    verticalArrangement = Arrangement.Center
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
<!-- /Column -->
<!-- Row -->
## Row
### X-ordered stack of children
Row is a layout that places its children in a horizontal sequence. It sizes its children to their preferred width and the height of the tallest child. It positions its children relative to its left edge and may optionally clip them if they extend beyond its right edge.
<!-- Code block -->
```kotlin
Row(
    modifier = Modifier.fillMaxSize(),
    horizontalArrangement = Arrangement.Center,
    verticalAlignment = Alignment.CenterVertically
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->

<!-- Box -->
## Box
### Z-ordered stack of children
Box is a layout that allows you to position its children in arbitrary positions. It sizes its children to their preferred size and positions them relative to its top left corner. It may optionally clip its children if they extend beyond its bounds.
<!-- Code block -->
```kotlin
Box(
    modifier = Modifier.fillMaxSize(),
    contentAlignment = Alignment.Center
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
<!-- Image -->
## Image
### Displays an image
Image is a layout that displays an image. It sizes itself to the intrinsic size of the image and positions itself relative to its top left corner. It may optionally clip the image if it extends beyond its bounds.
<!-- Code block -->
```kotlin
Image(
    painter = painterResource(id = R.drawable.ic_launcher_foreground),
    contentDescription = "Android Logo",
    modifier = Modifier
        .size(100.dp)
        .clip(CircleShape)
)
```
### Image content scale
The scale parameter allows you to specify how the image should be scaled to fit its bounds. The default value is ContentScale.Fit, which scales the image uniformly (maintaining the image's aspect ratio) so that both dimensions (width and height) of the image will be equal to or less than the corresponding dimension of the layout.

<!-- List of content scale -->
| ContentScale | Description |
| --- | --- |
| ContentScale.FillBounds | Scale the image uniformly (maintaining the image's aspect ratio) so that both dimensions (width and height) of the image will be equal to or larger than the corresponding dimension of the layout. |
| ContentScale.Fit | Scale the image uniformly (maintaining the image's aspect ratio) so that both dimensions (width and height) of the image will be equal to or less than the corresponding dimension of the layout. |
| ContentScale.Inside | Scale the image uniformly (maintaining the image's aspect ratio) so that both dimensions (width and height) of the image will be equal to or less than the corresponding dimension of the layout. If the image is smaller than the layout, then it will be placed in the center of the layout. |
| ContentScale.Crop | Scale the image uniformly (maintaining the image's aspect ratio) so that both dimensions (width and height) of the image will be equal to or larger than the corresponding dimension of the layout. The image will then be cropped to fit into the layout bounds. |
| ContentScale.FillWidth | Scale the image uniformly (maintaining the image's aspect ratio) so that its width will be equal to the width of the layout and its height will be equal to or less than the height of the layout. |
| ContentScale.FillHeight | Scale the image uniformly (maintaining the image's aspect ratio) so that its height will be equal to the height of the layout and its width will be equal to or less than the width of the layout. |
| ContentScale.None | Do not scale the image. |
<!-- /List of content scale -->
  



<!-- Code block -->
```kotlin
Image(
    painter = painterResource(id = R.drawable.ic_launcher_foreground),
    contentDescription = "Android Logo",
    modifier = Modifier
        .size(100.dp)
        .clip(CircleShape),
    contentScale = ContentScale.Crop
)
```
<!-- /Code block -->
### contentDescription
The contentDescription parameter is used by accessibility services to describe the image to visually impaired users. It is required for all images that convey meaning and should be left empty otherwise.
<!-- /Image -->

<!-- Spacer -->
## Spacer
### Adds space between components
Spacer is a layout that adds space between components. It sizes itself to the specified width and height and positions itself relative to its top left corner.
<!-- Code block -->
```kotlin
Row(
    modifier = Modifier.fillMaxSize(),
    horizontalArrangement = Arrangement.Center,
    verticalAlignment = Alignment.CenterVertically
) {
    Text(text = "Hello World!")
    Spacer(modifier = Modifier.width(10.dp))
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
<!-- /Spacer -->

<!-- Text -->
## Text
### Displays text
Text is a layout that displays text. It sizes itself to the size of the text and positions itself relative to its top left corner. It may optionally clip the text if it extends beyond its bounds.
<!-- Code block -->
```kotlin
Text(
    text = "Hello World!",
)
```

### Text style
The style parameter allows you to specify the style of the text. The default value is MaterialTheme.typography.body1.
<!-- Code block -->
```kotlin
Text(
    text = "Hello World!",
    style = TextStyle(
        color = Color.Red,
        fontSize = 20.sp,
        fontWeight = FontWeight.Bold,
        fontStyle = FontStyle.Italic,
        textAlign = TextAlign.Center,
        textDecoration = TextDecoration.Underline,
        letterSpacing = 2.sp,
        lineHeight = 20.sp,
        fontFamily = FontFamily.Serif,
        background = Color.Yellow,
        shadow = Shadow(
            color = Color.Black,
            offset = Offset(2f, 2f),
            blurRadius = 2f
        )
    )
)
```
<!-- /Code block -->

### Custom fonts
Create a new resource directory in the src/main/res directory of your project and name it font.
Copy the font files into the newly created directory.
<!-- Code block -->
```kotlin
Text(
    text = "Hello World!",
    style = TextStyle(
        fontFamily = FontFamily(
            Font(R.font.roboto_regular),
            Font(R.font.roboto_bold, FontWeight.Bold)
        )
    )
)
```
<!-- /Code block -->
<!-- /Text -->

<!-- Button -->
## Button
### Displays a clickable button
Button is a layout that displays a clickable button. It sizes itself to the size of the button and positions itself relative to its top left corner. It may optionally clip the button if it extends beyond its bounds.
<!-- Code block -->
```kotlin
Button(
    onClick = { /*TODO*/ },
    modifier = Modifier
        .padding(16.dp)
        .fillMaxWidth()
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
<!-- /Button -->

<!-- R class -->
## R class
### Resource class
The R class is an automatically generated class that contains references to all of your project's resources. It is generated by the Android build tools and is always located in the source package of your project. For example, if your project's package is com.example.myapp, then the R class will be located in the com.example.myapp package.

```kotlin
// Accessing a drawable resource
val drawable = R.drawable.ic_launcher_foreground
// Accessing a string resource
val string = R.string.app_name
// Accessing a color resource
val color = R.color.purple_200
// Accessing a font resource
val font = R.font.roboto_regular
```
<!-- /R class -->

<!-- modifier properties -->
## Modifiers
Modifiers are used to change the layout of the composable. They can be used to change the size, position, padding, background color, etc. of the composable.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier
        .fillMaxSize() // fill the entire screen
        .background(color = Color.Red)  // background color
        .padding(16.dp) // padding
        .clip(shape = RoundedCornerShape(8.dp)) // clip the corners
        .border(width = 2.dp, color = Color.Black, shape = RoundedCornerShape(8.dp)) // border
        .clickable(onClick = { /*TODO*/ })  // trigger an action on click
        .offset(x = 10.dp, y = 10.dp)   // offset the view
        .size(width = 100.dp, height = 100.dp)  // set the size of the view
        .rotate(45f)    // rotate the view
        .scale(1.5f)    // scale the view
        .alpha(0.5f)    // set the opacity of the view
        .shadow(8.dp, shape = RoundedCornerShape(8.dp)) // add a shadow to the view
        .graphicsLayer(
            rotationX = 45f,
            rotationY = 45f,
            scaleX = 1.5f,
            scaleY = 1.5f,
            translationX = 10.dp.toPx(),
            translationY = 10.dp.toPx(),
            alpha = 0.5f
        )
        .drawBehind {
            drawRect(color = Color.Red)
        }
        .drawWithContent {
            drawContent()
            drawRect(color = Color.Red)
        }
        .drawLayer(
            rotationX = 45f,
            rotationY = 45f,
            scaleX = 1.5f,
            scaleY = 1.5f,
            translationX = 10.dp.toPx(),
            translationY = 10.dp.toPx(),
            alpha = 0.5f
        )
        .drawWithCache {
            drawContent()
            drawIntoCanvas { canvas ->
                canvas.drawRect(Rect(0f, 0f, 100f, 100f), Paint().apply { color = Color.Red })
            }
        }
        .drawWithContent {
            drawContent()
            drawIntoCanvas { canvas ->
                canvas.drawRect(Rect(0f, 0f, 100f, 100f), Paint().apply { color = Color.Red })
            }
        }
        .drawWithCache {
            drawContent()
            drawIntoCanvas { canvas ->
                canvas.drawRect(Rect(0f, 0f, 100f, 100f), Paint().apply { color = Color.Red })
            }
        }
        .drawWithContent {
            drawContent()
            drawIntoCanvas { canvas ->
                canvas.drawRect(Rect(0f, 0f
        //More modifiers
[...]
```
### Important modifiers
#### fillMaxSize()
Fills the entire screen.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.fillMaxSize()
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### fillMaxSize(float)
Fills the entire screen with a percentage of the screen size.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.fillMaxSize(0.5f)
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### fillMaxWidth()
Fills the entire width of the screen.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.fillMaxWidth()
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### fillMaxHeight()
Fills the entire height of the screen.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.fillMaxHeight()
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### padding()
Adds padding to the composable.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.padding(16.dp)
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### padding(horizontal, vertical)
Adds padding to the composable.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.padding(horizontal = 16.dp, vertical = 8.dp)
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### padding(start, top, end, bottom)
Adds padding to the composable.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.padding(start = 16.dp, top = 8.dp, end = 16.dp, bottom = 8.dp)
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### background(color)
Sets the background color of the composable.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.background(color = Color.Red)
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### border(width, color, shape)
Adds a border to the composable.
<!-- Code block -->
```kotlin
Column(
    modifier = Modifier.border(width = 2.dp, color = Color.Black, shape = RoundedCornerShape(8.dp))
) {
    Text(text = "Hello World!")
}
```
<!-- /Code block -->
### weight()
Sets the weight of the composable.
Weight is used to determine the size of the composable when the parent composable is using a layout that supports weight. For example, a Row composable with two children, one with a weight of 1 and the other with a weight of 2, will take up 1/3 of the width of the parent composable.
<!-- Code block -->
```kotlin
Row(
    modifier = Modifier.fillMaxSize()
) {
    Text(text = "Hello World!", modifier = Modifier.weight(1f))
    Text(text = "Hello World!", modifier = Modifier.weight(2f))
}
```
<!-- /Code block -->


### More Modifier properties
| Property | Description |
| --- | --- |
| `align(Alignment)` | Aligns the composable relative to its parent. |
| `alignBy(AlignmentLine)` | Aligns the composable relative to its parent using an alignment line. |
| `alpha(Float)` | Sets the opacity of the composable. |
| `background(Color)` | Sets the background color of the composable. |
| `border(BorderStroke)` | Adds a border to the composable. |
| `border(BorderStroke, shape: Shape)` | Adds a border to the composable. |
| `clip(Shape)` | Clips the composable to the specified shape. |
| `clickable(onClick: () -> Unit)` | Triggers an action on click. |
| `drawBehind(onDraw: DrawScope.() -> Unit)` | Draws behind the composable. |
| `drawLayer(rotationX: Float, rotationY: Float, scaleX: Float, scaleY: Float, translationX: Float, translationY: Float, alpha: Float)` | Draws the composable using a layer. |
| `drawWithCache(onDraw: DrawScope.() -> Unit)` | Draws the composable using a cache. |
| `drawWithContent(onDraw: DrawScope.() -> Unit)` | Draws the composable with content. |
| `fillMaxHeight()` | Fills the composable to the height of its parent. |
| `fillMaxSize()` | Fills the composable to the size of its parent. |
| `fillMaxWidth()` | Fills the composable to the width of its parent. |
| `graphicsLayer(rotationX: Float, rotationY: Float, scaleX: Float, scaleY: Float, translationX: Float, translationY: Float, alpha: Float)` | Draws the composable using a graphics layer. |
| `height(Height)` | Sets the height of the composable. |
| `offset(x: Dp, y: Dp)` | Offsets the composable. |
| `padding(Insets)` | Adds padding to the composable. |
| `padding(start: Dp, top: Dp, end: Dp, bottom: Dp)` | Adds padding to the composable. |
| `padding(horizontal: Dp, vertical: Dp)` | Adds padding to the composable. |
| `padding(all: Dp)` | Adds padding to the composable. |
| `paddingFromBaseline(FirstBaselineToTop, LastBaselineToBottom)` | Adds padding to the composable from the baseline. |
| `paddingFromBaseline(top: Dp, bottom: Dp)` | Adds padding to the composable from the baseline. |
| `paddingFromBaseline(top: Dp)` | Adds padding to the composable from the baseline. |
| `paddingFromBaseline(bottom: Dp)` | Adds padding to the composable from the baseline. |
| `rotate(degrees: Float)` | Rotates the composable. |
| `scale(scale: Float)` | Scales the composable. |
| `shadow(elevation: Dp, shape: Shape)` | Adds a shadow to the composable. |
| `size(Width, Height)` | Sets the size of the composable. |
| `size(width: Dp, height: Dp)` | Sets the size of the composable. |
| `size(width: Dp)` | Sets the size of the composable. |
| `size(height: Dp)` | Sets the size of the composable. |
| `width(Width)` | Sets the width of the composable. |

<!-- end list -->

## The Box Model
In web development, the CSS box model refers to how HTML elements are modeled in browser engines and how the dimensions of those HTML elements are derived from CSS properties. It is a fundamental concept for the composition of HTML webpages.

In Jetpack Compose, the box model is a fundamental concept for the composition of UI elements. The box model is a set of properties that define the size and position of a composable. The box model is composed of the following properties:

| Property | Description |
| --- | --- |
| `width` | The width of the composable. |
| `height` | The height of the composable. |
| `padding` | The padding of the composable. |
| `border` | The border of the composable. |

## Dp and Sp

### Display Pixels (dp)
Display pixels (dp) are a unit of measurement that is used to define the size of UI elements. The dp unit is relative to the density of the screen. For example, on a high-density screen, 1 dp is equal to 1 pixel. On a low-density screen, 1 dp is equal to 2 pixels.

```kotlin
Text(
    text = "Hello World!",
    modifier = Modifier.padding(16.dp)
)
```

### Scale Pixels (sp)
Scale pixels (sp) are a unit of measurement that is used to define the size of text. The sp unit is relative to the density of the screen. For example, on a high-density screen, 1 sp is equal to 1 pixel. On a low-density screen, 1 sp is equal to 2 pixels.

```kotlin
Text(
    text = "Hello World!",
    fontSize = 16.sp
)
```








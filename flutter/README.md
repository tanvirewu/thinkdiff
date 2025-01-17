# Flutter

- [Background](#background)
- [Widget](#widget)
- [Layout in Flutter](https://flutter.dev/docs/development/ui/layout)
- [Animated Container](#animated-container)
- [Animated Opacity](#animated-opacity)
- [Navigation Drawer](#navigation-drawer)

####  Background

Flutter is a cross-platform mobile app development framework by Google. It used Dart programming language. Flutter compiles to actual native code for (ARM) and is rendered using a library named skia.

- Flutter also supports hot reloading for faster development
- A flutter app is represented by a `widget tree` similar to the `DOM` on the browser.

-  Flutter app uses an `event loop`. Which is a background infinite loop periodically wake up and checks the `event queue` to see if there is any task assigned. If the **CPU is idle**, the event loop puts the task onto the `run stack`. 


### Widget

Flutter is a reactive library like ReactJS on Web. In flutter, ***everything is a widget*** and every widget is a dart class. Using widget we create view.

#### Widgets are 2 types:

1. Stateless - it's immutable
2. Statefull - tracks it's own internal state

#### Some common widgets are:

- Layout - `Container, Row, Column, Scaffold, Stack`
- Structures - `Button, Toast, MenuDrawer`
- Styles - `TextStyle, Color`
- Animations - `FadeInPhoto, transformations`
- Position, Alignment - `Center, Padding`

##### Flutter favors composition over class inheritance

- Every widget must have a `build` method which must returns `widget`
- `BuildContext` contains the reference of the widget location in the widget tree

##### Stateless widget example

```dart
class MyApp extends StatelessWidget {                      
  @override  
  Widget build(BuildContext context) {                     
    return MaterialApp(                                    
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Flutter Demo Home Page'),   
    );
  }
}
```

- Every `StatefulWidget` must have a `createState`method which returns a `State`object
- Every `StatefulWidget` has an associated `State` object, which have a `build`method
- Using `setState(() { })` method state object uses to manage internal state

##### Stateful widget example

```dart
class MyHomePage extends StatefulWidget {
@override
  _MyHomePageState createState() => _MyHomePageState();   
}

class _MyHomePageState extends State<MyHomePage> { 
  int _counter = 0;
  
  @override
  Widget build(BuildContext context) { 
    return Container();
  }
  
  void increment() {
     setState(() {
      _counter += 1;
     });
  }
}
```

### Animated Container

`ÀnimatedContainer` widget when change the properties it shows animation. It's similar like the `Container` widget. It's called implicit animation. [Code](https://github.com/mahmudahsan/thinkdiff/blob/master/flutter/small_demo/animation_container/lib/main.dart)

### Animated Opacity
If we need a widget to fade in and fade out, we can use `AnimatedOpacity` widget. Using `opacity` and `duration` properties we can change the opacity with animation.

```dart
       AnimatedOpacity(
          opacity: _isVisible ? 1 : 0,
          duration: Duration(milliseconds: 500),
          child: Container(
            height: 100,
            width: 100,
            color: Colors.green,
          ),
        ),
      ),

```
[Sample App](https://github.com/mahmudahsan/thinkdiff/blob/master/flutter/small_demo/fade_widget/lib/main.dart)

### Navigation Drawer

To show a navigation drawer within material app, `Scaffold` has a `drawer` property where we can initiate `Drawer()` widget. [Code](https://github.com/mahmudahsan/thinkdiff/blob/master/flutter/small_demo/drawer/lib/main.dart)


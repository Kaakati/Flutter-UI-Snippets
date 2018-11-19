# Flutter Material UI Arrangment Snippets
Snippets for Material UI in Flutter

### MaterialApp
```dart
MaterialApp(
  title: 'My App',
  home: Scaffold(... // Scaffold,
);
```

### Scaffold & AppBar
Scaffold: Creates a visual scaffold for material design widgets.
Appbar: Creates a material design app bar.

```dart
Scaffold(
appBar: AppBar(
  title: Text('App Bar Title'),
  elevation: 0.4, // Elevation Shadow.
  // Use for Custom Menus, otherwise check Drawer widget.
  leading: IconButton(
    icon: new Icon(Icons.menu),
    onPressed: () { print('Menu Button Pressed') },
  ),
),
// Use SafeArea Creates a widget that avoids operating system interfaces. 
body: SafeArea(
  minimum: EdgeInsets.all(15),
  child: // A Widget,
)
```

### Column
Creates a vertical array of children.

```dart
Column(
  crossAxisAlignment: CrossAxisAlignment.stretch,
  children: <Widget>[
    new Container(
      height: 44.0,
      child: new FlatButton(
        color: Colors.blue,
        child: Text('Login'),
        onPressed: () {
          print('Button Pressed');
        },
      ),
    ),
  ],
);
```

### Container
Creates a widget that combines common painting, positioning, and sizing widgets.

```dart
Container(
  height: 60.0,
  width: 60.0,
  decoration: new BoxDecoration(
    color: Colors.green,
    borderRadius: new BorderRadius.circular(50.0),
  ),
  child: new Icon(Icons.home, color: Colors.white),
);
```

### Expanded
Creates a widget that expands a child of a `Row`, `Column`, or `Flex` expand to fill the available space in the main axis.

```dart
Expanded(
  child: Text('Lorem Ipsum'),
)
```

### SizedBox
Can be used as a spacer between elements.

```dart
SizedBox(height: 12.0)
```

### Textfield

```dart
TextField(
  decoration: 
  (
    filled: true,
    labelText: 'Username',
  ),
),
// spacer
SizedBox(height: 12.0),
// [Password]
TextField(
  decoration: InputDecoration(
    filled: true,
    labelText: 'Password',
  ),
  obscureText: true,
)
```

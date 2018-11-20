# Flutter Material UI Snippets
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
  decoration: InputDecoration(
    fillColor: Colors.transparent, // Sets Fill Color
    filled: false, // isFilled?
    labelText: 'Username', // Placeholder
    labelStyle: TextStyle(
      color: Colors.grey // Placeholder Color
    )
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
  obscureText: true, // Secure Input?
)
```

### Form

```dart
enum FormType { login, register }

// final formKey = new GlobalKey<FormState>();

Form(
  key: this.formKey, // Form Identifier
  child: new Column(
    crossAxisAlignment: CrossAxisAlignment.stretch,
    children: _buildInputs() + _buildFormActions(),
  ),
)

List<Widget> _buildInputs() {
  return [
    new TextFormField(
      decoration: new InputDecoration(labelText: 'Email'),
      validator: (value) => value.isEmpty ? 'Email can\'t be empty' : null,
      onSaved: (value) => this._email = value,
    ),
    new TextFormField(
      decoration: new InputDecoration(labelText: 'Password'),
      obscureText: true,
      validator: (value) => value.isEmpty ? 'Password can\'t be empty' : null,
      onSaved: (value) => this._password = value,
    ),
    new SizedBox(height: 20.0),
  ];
}

List<Widget> _buildFormActions() {
  if (_formType == FormType.login) {
    return [
      new RaisedButton(
          child: Text('Login', style: new TextStyle(fontSize: 16)),
          onPressed: validateAndSubmit),
      new SizedBox(height: 20.0),
      new FlatButton(
          child: Text('Not Registered? Create Account.',
              style: new TextStyle(fontSize: 14.0)),
          onPressed: moveToRegister),
    ];
  } else {
    return [
      new RaisedButton(
          child: Text('Create an account', style: new TextStyle(fontSize: 16)),
          onPressed: validateAndSubmit),
      new SizedBox(height: 20.0),
      new FlatButton(
          child: Text('Already Registered? Login.',
              style: new TextStyle(fontSize: 14.0)),
          onPressed: moveToLogin),
    ];
  }
}
```

### Dismissible
Slide to Dismiss / Delete on ListView
```dart
class MyHome extends StatelessWidget {
  //geneates dummy list
  // lenght and data
  final List<String> items = new List<String>.generate(30, (i) => "Items $i");
  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
        title: new Text("Swipe to Dismiss"),
      ),
      body: new ListView.builder(
        itemCount: items.length,
        itemBuilder: (context, int index) {
          final item = items[index];
          return new Dismissible(
            key: new Key(item),
            onDismissed: (direction) {
              items.removeAt(index);
              Scaffold.of(context).showSnackBar(new SnackBar(
                    content: new Text("Item Dismissed"),
                  ));
            },
            background: new Container(color:Colors.red),
            child: new ListTile(
              title: new Text("$item"),
            ),
          );
        },
      ),
    );
  }
}
```

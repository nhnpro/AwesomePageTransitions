# Awesome Page Transitions example

## Using
```dart
import 'package:awesome_page_transitions/awesome_page_transitions.dart';
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Awesome Page Transitions Demo',
      home: MyHomePage(title: 'Awesome Page Transitions Demo'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Container(
        alignment: Alignment.center,
        color: Colors.yellow,
        child: RaisedButton(
          color: Colors.red,
          child: Text("Open"),
          onPressed: () => Navigator.push(
            context,
            AwesomePageRoute(
              transitionDuration: Duration(milliseconds: 600),
              exitPage: widget,
              enterPage: SecondScreen(),
              transition: CubeTransition(),
            ),
          ),
        ),
      ),
    );
  }
}

class SecondScreen extends StatefulWidget {
  @override
  _SecondScreenState createState() => _SecondScreenState();
}

class _SecondScreenState extends State<SecondScreen> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Second Screen"),),
      body: Container(
        alignment: Alignment.center,
        color: Colors.red,
        child: RaisedButton(
          color: Colors.yellow,
          onPressed: () => Navigator.pop(context),
          child: Text("Go Back"),
        ),
      ),
    );
  }
}
```
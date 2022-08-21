# flutter_d12_dynamic_list

- main.dart
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatefulWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  final _users = List.filled(100, "Zein");

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: DefaultTabController(
        length: 2,
        child: Scaffold(
          backgroundColor: Colors.white70,
          appBar: AppBar(
            bottom: const TabBar(
              tabs: [
                Text("List"),
                Text("Grid"),
              ],
            ),
          ),
          body: TabBarView(
            children: [
              _contentListView(),
              _contentGridView(),
            ],
          ),
        ),
      ),
    );
  }

  Widget _contentListView() {
    return ListView.builder(
      itemCount: _users.length,
      itemBuilder: (context, index) {
        return Card(
          child: ListTile(
            title: Text('Data ' + index.toString()),
            onTap: () {
              print("hello $index");
            },
          ),
        );
      },
    );
  }

  Widget _contentGridView() {
    return GridView.builder(
      itemCount: _users.length,
      gridDelegate:
          const SliverGridDelegateWithFixedCrossAxisCount(crossAxisCount: 3),
      itemBuilder: (context, index) {
        return Card(
          child: GridTile(
            child: Center(
              child: Text('Data ' + _users[index]),
            ),
          ),
        );
      },
    );
  }
}
```

---

```
Copyright 2022 M. Fadli Zein
```
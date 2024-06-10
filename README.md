



# Dart JSON Data Handling with List of Maps and Factory Constructors

This project demonstrates how to handle JSON data in Dart using lists of maps and factory constructors. It covers parsing JSON data, creating Dart objects from JSON, and converting Dart objects back to JSON.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [Parsing JSON Data](#parsing-json-data)
  - [Creating Dart Objects](#creating-dart-objects)
  - [Converting Dart Objects to JSON](#converting-dart-objects-to-json)
- [Example](#example)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Introduction

This repository provides a simple and effective way to manage JSON data in Dart applications using lists of maps and factory constructors. This approach is particularly useful for developers working with structured data from APIs or other sources in their Dart applications.

## Features

- Parse JSON data into Dart objects.
- Convert Dart objects back to JSON.
- Utilize factory constructors for clean and maintainable code.
- Example code to demonstrate functionality.

## Getting Started

### Prerequisites

Before you begin, ensure you have met the following requirements:

- Dart SDK installed on your machine (version 2.12 or higher).
- Basic understanding of the Dart programming language.

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/dart-json-handling.git
    ```

2. Navigate to the project directory:

    ```bash
    cd dart-json-handling
    ```

## Usage

### Parsing JSON Data

To parse JSON data into Dart objects, use the `fromJson` factory constructor:

```dart
import 'dart:convert';

class YourModel {
  final String name;
  final int age;

  YourModel({required this.name, required this.age});

  factory YourModel.fromJson(Map<String, dynamic> json) {
    return YourModel(
      name: json['name'],
      age: json['age'],
    );
  }
}
```

### Creating Dart Objects

You can create Dart objects by calling the `fromJson` constructor:

```dart
String jsonString = '{"name": "John Doe", "age": 30}';
Map<String, dynamic> userMap = jsonDecode(jsonString);
YourModel user = YourModel.fromJson(userMap);
```

### Converting Dart Objects to JSON

To convert a Dart object back to JSON, implement a `toJson` method in your class:

```dart
class YourModel {
  final String name;
  final int age;

  YourModel({required this.name, required this.age});

  factory YourModel.fromJson(Map<String, dynamic> json) {
    return YourModel(
      name: json['name'],
      age: json['age'],
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'name': name,
      'age': age,
    };
  }
}
```

## Example

Here's a complete example to demonstrate the functionality:

```dart
import 'dart:convert';

void main() {
  // JSON string containing a list of objects
  String jsonString = '[{"name": "John Doe", "age": 30}, {"name": "Jane Smith", "age": 25}]';
  
  // Decode JSON string to a list of dynamic objects
  List<dynamic> jsonList = jsonDecode(jsonString);
  
  // Convert JSON list to a list of YourModel objects
  List<YourModel> users = jsonList.map((json) => YourModel.fromJson(json)).toList();

  // Print each user's data
  for (var user in users) {
    print('Name: ${user.name}, Age: ${user.age}');
  }

  // Convert the list of YourModel objects back to JSON
  String encodedJson = jsonEncode(users.map((user) => user.toJson()).toList());
  print(encodedJson);
}

class YourModel {
  final String name;
  final int age;

  YourModel({required this.name, required this.age});

  factory YourModel.fromJson(Map<String, dynamic> json) {
    return YourModel(
      name: json['name'],
      age: json['age'],
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'name': name,
      'age': age,
    };
  }
}
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [Dart Documentation](https://dart.dev/guides)
- [JSON Handling in Dart](https://dart.dev/tutorials/web/json)
```

This README provides a comprehensive and clear guide for handling JSON data in Dart using lists of maps and factory constructors. It includes installation instructions, code examples, and detailed explanations.

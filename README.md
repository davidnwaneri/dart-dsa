# dart-dsa
Data Structure and Algorithm examples in Dart


## FizzBuzz

Given a number n, for each integer i in the range from 1 to n inclusive, print one value per line as follows:

- If i is a multiple of both 3 and 5, print FizzBuzz.
- If i is a multiple of 3 (but not 5), print Fizz.
- If i is a multiple of 5 (but not 3), print Buzz.
- If i is not a multiple of 3 or 5, print the value of i.

```dart
import 'dart:io';
import 'dart:convert';
import 'dart:async';
import 'dart:math';

void main() {
  int n = int.parse(stdin.readLineSync()!.trimRight());

  fizzBuzz(n);
}

void fizzBuzz(int n) {
  for (var i = 1; i <= n; i++) {
    final isMultipleOf5 = isMultiple(i, of: 5);
    final isMultipleOf3 = isMultiple(i, of: 3);

    if (isMultipleOf3 && isMultipleOf5) {
      print('FizzBuzz');
    } else if (isMultipleOf3 && !isMultipleOf5) {
      print('Fizz');
    } else if (!isMultipleOf3 && isMultipleOf5) {
      print('Buzz');
    } else if (!isMultipleOf3 && !isMultipleOf5) {
      print(i);
    }
  }
}

bool isMultiple(int n, {required int of}) => n % of == 0;
```

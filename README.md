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

## Maximum sum of Subarray of size K

You are given an array of integers `arr` and an integer `k`. Find the maximum sum of any contiguous subarray of size `k`.
Example:
Input: arr = [2, 1, 5, 1, 3, 2], k = 3
Output: 9

Explanation:
Subarrays of size 3 are:
```
[2, 1, 5] => sum = 8
[1, 5, 1] => sum = 7
[5, 1, 3] => sum = 9
[1, 3, 2] => sum = 6
```
Maximum sum is 9.

### Solution
```dart
void main() {
  const array = [2, 1, 5, 1, 3, 2];
  const subArraySize = 3;

  final maxSum = calculateSum(array: array, subArraySize: subArraySize);
  print('Max sum is $maxSum');
}

int calculateSum({required List<int> array, required int subArraySize}) {
  int maxSum = 0;

  if (array.length < subArraySize) return maxSum;

  for (int i = 0; i < (array.length - (subArraySize - 1)); i++) {
    final subArray = array.sublist(i, subArraySize + i);

    final sumOfSubArray = subArray.reduce((current, next) => current + next);
    if (sumOfSubArray > maxSum) maxSum = sumOfSubArray;
    print('SubArray: $subArray => Sum = $sumOfSubArray');
  }

  return maxSum;
}
```

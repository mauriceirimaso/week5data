# week5data

import 'dart:io';
import 'dart:convert';

void main() {
  // String Manipulation
  stdout.write("Enter a string: ");
  String input = stdin.readLineSync()!;

  String capitalized = capitalizeFirstLetter(input);
  String reversed = reverseString(input);
  int length = input.length;

  print("Capitalized: $capitalized");
  print("Reversed: $reversed");
  print("Length: $length");

  // Collections (List, Set, Map)
  List<String> resultsList = [];
  Set<String> uniqueResultsSet = {};
  Map<String, DateTime> logMap = {};

  resultsList.add(capitalized);
  resultsList.add(reversed);
  uniqueResultsSet.add(capitalized);
  uniqueResultsSet.add(reversed);

  // Log results with date and time
  logMap[capitalized] = DateTime.now();
  logMap[reversed] = DateTime.now();

  print("List of Results: $resultsList");
  print("Unique Results Set: $uniqueResultsSet");
  print("Log Map: $logMap");

  // File Handling
  writeToFile('results.txt', resultsList);
  readFromFile('results.txt');

  // Date and Time Manipulation
  DateTime now = DateTime.now();
  DateTime futureDate = now.add(Duration(days: 5));
  print("Current Date: $now");
  print("Future Date (5 days later): $futureDate");
}

String capitalizeFirstLetter(String str) {
  if (str.isEmpty) return str;
  return str[0].toUpperCase() + str.substring(1);
}

String reverseString(String str) {
  return str.split('').reversed.join('');
}

void writeToFile(String filename, List<String> data) {
  File file = File(filename);
  file.writeAsStringSync(data.join('\n'));
  print("Data written to $filename");
}

void readFromFile(String filename) {
  try {
    File file = File(filename);
    String contents = file.readAsStringSync();
    print("Data read from $filename:\n$contents");
  } catch (e) {
    print("Error reading file: $e");
  }
}

# Strings and Numbers

Conversions and manipulations between strings, characters, and numbers.

## String and Number Conversions

- **Number to String:**
  ```cpp
  to_string(num)
  ```
- **String to Integer:**
  ```cpp
  stoi(str)
  ```
- **String to Long Long:**
  ```cpp
  stoll(str)
  ```
- **String to Double:**
  ```cpp
  stod(str)
  ```

## Character and Integer Conversions

- **Character to Integer:**
  ```cpp
  char c = '7';
  int num = c - '0'; // num is 7 (int) now
  ```

- **Integer to Character:**
  ```cpp
  int num = 5;
  char c = num + '0'; // c is now '5' (char)
  ```

## Character Case Conversion

- **Uppercase to Lowercase:**
  ```cpp
  char lower = upper + 32;
  // or
  tolower(c);
  ```

- **Lowercase to Uppercase:**
  ```cpp
  char upper = lower - 32;
  // or
  toupper(c);
  ```

## String Functions

- **Substring:**
  ```cpp
  s.substr(pos, len);
  ```
- **Find Substring:**
  ```cpp
  s.find(substring); // Returns starting position, or string::npos if not found
  ```

## Character Checking (from `<cctype>`)

- **Check if alphabet letter:**
  ```cpp
  isalpha(c)
  ```
- **Check if digit:**
  ```cpp
  isdigit(c)
  ```
- **Check if alphanumeric:**
  ```cpp
  isalnum(c)
  ```

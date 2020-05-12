# Dart Tutorial

- Hello World Program
  ```dart
  void main() {
      print('Hello World');
  }
  ```
- Basic dart program

  ```dart
  int add(int a, int b) {
      return a + b;
  }

  void main() {
      int a = 10, b = 20;
      print(add(a, b));
  }
  ```

- Variables
  ```dart
  var name = 'Nuclei';
  const name = 'Nuclei';
  String name = 'Nuclei'
  ```
- Built-In Types

  - `int`
    ```dart
    int categoryId = 10;
    ```
  - `double`
    ```dart
    double pie = 3.14;
    ```
  - `string`
    ```dart
    string name = 'Nuclei';
    ```
  - `bool`
    ```dart
    bool is5GreaterThan10 = 5 > 10;
    ```
  - `list` (generics support)
    ```dart
    List<int> fiboSeries = [0, 1, 1, 2, 3, 5];
    print(fiboSeries[0]);
    ```
  - `sets` (generics support)
    ```dart
    Set<String> colors = {
        'red',
        'green',
        'orange'
    }
    ```
  - `map` (generics support)

    ```dart
    Map<int, String> numSpellings = {
        1: 'One',
        2: 'Two',
        3: 'Three'
    }

    print('Spelling for 1 is ${numSpellings[1]}');
    ```

- If-Else
  ```dart
  if (isValidUser) {
    print('Welcome!');
  } else {
    print('Please find a door!');
  }
  ```
- Switch
  ```dart
  switch(colors) {
      case 'red':
        print('Strawberries are red');
        break;
      case 'black':
        print('Black currant is black, I guess?');
        break;
      default:
        print('I have never seen such a color before');
  }
  ```
- Loops
  - `for`
    ```dart
    for (int i = 0; i < 10; ++i) {
        print(i);
    }
    ```
  - `for`-`in`
    ```dart
    List<int> numbers = [1, 2, 3, 4];
    for (int number in numbers) {
        print(number);
    }
    ```
  - `forEach`
    ```dart
    List<int> numbers = [1, 2, 3, 4];
    numbers.forEach((number) => print(number));
    ```
  - `while`
    ```dart
    int i = 0;
    while (i < 10) {
        print(i++);
    }
    ```
  - `do`-`while`
    ```dart
    int i = 0;
    do {
        print(i++);
    } while(i < 10);
    ```
- Functions (`Function`)

  ```dart
  int add(int a, int b) {
      return a + b;
  }

  add(10, 20);
  ```

  - arrow syntax

    ```dart
    int add(int a, int b) => a + b;

    add(10, 20);
    ```

  - postitional params

    ```dart
    int add(int a, int b) => a + b;

    add(10, 20);
    ```

  - named params

    ```dart
    int subract({int firstNumber, int secondNumber}) {
        return firstNumber + secondNumber;
    }

    subtract(firstNumber: 10, secondNumber: 20);
    ```

  - optional params
    - positional optional params
    ```dart
    int add(int a, [int b]) {
        if (b != nil) {
            return a + b;
        } else {
            return a + 10;
        }
    }
    ```
    - named optional params
    ```dart
    int add({int a, int b}) {
        if (a == nil && b == nil) {
            return 10;
        } else if (b == nil) {
            return a + 10;
        } else {
            return 10 + b;
        }
    }
    ```
  - default params

    - positional default params

    ```dart
    int add(int a, [int b = 10]) {
        return a + b;
    }

    add(10);
    add(10, 20);
    ```

    - named default params

    ```dart
    int add({int a, int b = 10}) {
        return a + b;
    }
    ```

  - `@required` annotation

    ```dart
    import 'package:meta/meta.dart';

    int add({@required int a, @required int b}) {
        return a + b;
    }
    ```

- Functions As First-Class Objects

  ```dart
  void add10AndPrint(int a) {
      print(a + 10);
  }

  List<int> numbers = [1, 2, 3, 4];

  numbers.forEach(add10AndPrint);
  ```

- Anonymous Functions

  ```dart
  List<int> numbers = [1, 2, 3, 4];

  numbers.forEach((number) {
      print(a + 10);
  });

  numbers.forEach((number) => print(a + 10));
  ```

- `assert`
  ```dart
  int a = 10, b = 20;
  assert(a < b);
  ```
- Classes

  ```dart
  class Bank {
      int id;
      String name;
      String logoURL;

      int getId() {
          return id;
      }

      String getName() {
          return name;
      }

      String logoURL;

      Bank({
          @required int id,
          @required String name,
          @required String logoURL
      }) {
          this.id = id;
          this.name = name;
          this.logoURL = logoURL;
      }
  }
  ```

  - members
    - private
    ```dart
    class Bank {
        int _id; // _ indicated package private variable
        String _name;
    }
    ```
    - non-private
    ```dart
    class Bank {
        int id; // indicates is public variable
        String name;
    }
    ```
  - constructors

    - unnamed constructor

    ```dart
    class Bank {
        int id;
        String name;
        String logoURL:

        Bank({
            @required this.id,
            @required this.name;
            @required this.logoURL;
        });
    }
    ```

    - named constructor

    ```dart
    class Bank {
        int id;
        String name;
        String countryCode;
        String logoURL;

        Bank.indian({this.id, this.name, this.logoURL}) {
            this.countryCode = "+91";
        }

        Bank.gulf({this.id, this.name, this.logoURL}) {
            this.countryCode = "+12";
        }
    }
    ```

  - initializer list

    ```dart
    class CartesianPoint {
        double x, y;

        CartesianPoint(this.x, this.y);

        // CartesianPoint(double r, double theta): x = r*cos(theta), y = r*sin(theta)

        CartesianPoint.fromPolarCoordinates(double r, double theta): x = r*cos(theta), y = r*sin(theta);
    }
    ```

  - constructor redirection

    ```dart
    class CartesianPoint {
        double x, y;
        CartesianPoint(this.y, this.y);

        CartesianPoint({double y}) : this(0, y);
        CartesianPoint({double x}) : this(x, 0);
        CartesianPoint(): this(0, 0);
    }
    ```

  - `factory` constructor

    ```dart
    class Logger {
      final String name;
      bool mute = false;

      // _cache is library-private, thanks to
      // the _ in front of its name.
      static final Map<String, Logger> _cache =
          <String, Logger>{};

      factory Logger(String name) {
        return _cache.putIfAbsent(
            name, () => Logger._internal(name));
      }

      Logger._internal(this.name);

      void log(String msg) {
        if (!mute) print(msg);
      }
    }
    ```

  - getters and setters

    ```dart
    class CartesianPoint {
        double x, y, midPoint;
        CartesianPoint(this.x, this.y): midPoint = (x + y) / 2;

        double get r {
            double sumOfSquares = x * x + y * y;

            return math.sqrt(sumOfSquares);
        }

        double get theta => math.atan(y / x);

        void set x(double x) {
            this.x = x;
            this.midPoint = (x + y) / 2;
        }

        void set y(double y) {
            this.y = y;
            this.midPoint = (x + y) / 2;
        }
    }
    ```

  - abstract methods and interfaces

    ```dart
    abstract class Bank {
      void makeSales();
    }

    class IndianBank implements Bank {
      @override
      void makeSales() {
        print('Making sales...');
      }
    }
    ```

  - implicity interfaces

  ```dart
  class Person {
    final String _name;

    Person(this._name);

    String greet(String who) => 'Hello, $who. I am $_name.';
  }

  class Impostor implements Person {
    get _name => '';

    String greet(String who) => 'Hi $who. Do you know who I am?';
  }
  ```

  - inheritances via `extends`

    ```dart
    abstract class Bank {
      void makeSales();
    }

    class IndianBank extends Bank {
      @override
      void makeSales() {
        print('Making sales...');
      }
    }
    ```

  - `overriding` methods

    ```dart
    abstract class Bank {
      void makeSales();
    }

    class IndianBank extends Bank {
      @override
      void makeSales() {
        print('Making sales...');
      }
    }
    ```

  - operator overriding

    ```dart
    class Vector {
      final int x, y;

      Vector(this.x, this.y);

      Vector operator +(Vector v) => Vector(x + v.x, y + v.y);
      Vector operator -(Vector v) => Vector(x - v.x, y - v.y);
    }
    ```

  - `noSuchMethod()`
    ```dart
    class A {
      // Unless you override noSuchMethod, using a
      // non-existent member results in a NoSuchMethodError.
      @override
      void noSuchMethod(Invocation invocation) {
        print('You tried to use a non-existent member: ' +
            '${invocation.memberName}');
      }
    }
    ```

- Special Operators

  - Cascade (..)

    ```dart
    class Bank {
      int id = 1;
      String name = "Indian Name";
      String countryCode = "+91";
    }

    Bank bank = Bank()
                ..id = 2
                ..name = "Gulf bank";
    ```

  - Spread (...)

    ```dart
    List<String> supportStaff = [
      'A',
      'B'
    ];

    List<String> Staff = [
      ...supportStaff,
      'C',
      'D'
    ]; // ['A', 'B', 'C', 'D']
    ```

  - Conditional Member Access (?.)

  ```dart
  class Bank {
    final int id;
    final String name;

    Bank({this.id, this.name});
  }

  void main() {
    Bank bank = getBank();
    print(bank?.name); // bank.name gets evaluated to `null` if bank is empty
  }
  ```

  - If Null (??)

  ```dart
  class Bank {
    final int id;
    final String name;

    Bank({this.id, this.name});
  }

  void main() {
    Bank bank = getBank();
    print(bank?.name ?? 'No Bank Found'); // bank.name gets evaluated to `null` if bank is empty
  }
  ```

- Exception Handling

  - `try`
  - `catch`
  - `on`-`catch`
  - `finally`

  ```dart
  try {
    bank.makePayment();
  } on InsufficientFunds {
    // handle this case
  } on MonthlyLimitReached catch (e) {
    // handle this case
  } catch (e) {
    // general case
  } finally {
    bank.closeTransaction();
  }
  ```

  - `throw`

  ```dart
  class Bank {
    //...
    void makePayments() {
      if (insuffienctFunds()) {
        throw InsufficientFunds();
      } else if (monthlyLimitReached()) {
        throw MonthlyLimitReached(monthlyLimit: 1000);
      } else if (bankSecretIssue()) {
        throw "Unknow issue occured";
      } else {
        // proceed to make payment
      }
    }
  }
  ```

- Extensions

  ```dart
  extension NumberParsing on String {
    int parseInt() {
      return int.parse(this);
    }
    // ···
  }

  extension on String {
    String get localized {
      // some localization logic
    }
  }

  void main() {
    print("Process To Pay".localized);
  }
  ```

- Enums

  ```dart
  enum ViewPresentationStyles {
    leftPush, rightPush, bottomModal, topModal, present
  }

  ViewPresentationStyles.leftPush
  ```

- Asynchronous supports

  ```dart
  Future<String> getToken() async {
    // start querying for token
    String token = await backend.getToken();

    return token;
  }

  void main() async {
    String token = await getToken(); // blocking call.

    // executes after the above call returns.
    print(token);
  }
  ```

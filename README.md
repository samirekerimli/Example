/* 1. Variable types and declarations
  void main(){
  variablesDemo();
}

void variablesDemo() {
  int age = 20;
  double height = 1.75;
  bool isStudent = true;
  String name = 'Aysel';

  print('Name: $name, Age: $age, Height: $height, Student: $isStudent');
}*/

/* 2. Function with return value and parameters
  
  int add(int a, int b) {
  return a + b;
}
void main(){
  int result=add(5,6);
  print('result:$result');
}

3. Function with optional named parameters and default values
 void greetUser({String name = 'Guest'}) {
  print('Welcome, $name!');
}

void main() {
  greetUser();
  greetUser(name:'Aysel');

}

void greetUser({String name = 'Guest',String age='29'}) {
  print('Welcome, $name!,$age');
}

void main() {
  greetUser();
  greetUser(name:'Aysel',age:'27');

}
5. if-else condition example

void main() {
  int score = 85;
  String grade = gradeLetter(score);
  print('Bal: $score, Qiymət: $grade'); 
}
String gradeLetter(int score) {
  if (score >= 90) return "A";
  else if (score >= 80) return "B";
  else if (score >= 70) return "C";
  else if (score >= 60) return "D";
  else return "F";
}

 4. Null safety with nullable types
void checkEmail(String? email) {
  print('Email is: ${email ?? "No email provided"}');
}

void main() {
  checkEmail("example@gmail.com"); 
  checkEmail(null); 
}

6. switch-case example
String getDayType(String day) {
  switch (day) {
    case 'Saturday':
    case 'Sunday':
      return 'Weekend';
    case 'Monday':
    case 'Tuesday':
    case 'Wednesday':
    case 'Thursday':
    case 'Friday':
      return 'Weekday';
    default:
      return 'Invalid day';
  }
}
void main() {
  print('Friday is a ${getDayType("Friday")}');
  print(getDayType('Monday'));  
  print(getDayType('Funday'));   
}


2.1 List Transformations Examples
void doubleNumbers() {
  List<int> nums = [1, 2, 3, 4];
  var doubled = nums.map((n) => n * 2).toList();
  print(doubled); 
void main() {
  doubleNumbers();
  
}



void filterNumbers() {
  List<int> nums = [2, 4, 6, 8, 10];
  var filtered = nums.where((n) => n >= 5).toList();
  print(filtered); // [6, 8, 10]
}
void main(){
  filterNumbers();
  
}


void sumWithReduce() {
  List<int> nums = [1, 2, 3, 4];
  var sum = nums.reduce((a, b) => a + b);
  print(sum); 
}
void main(){
  sumWithReduce();



void productWithFold() {
  List<int> nums = [2, 3, 4];
  var product = nums.fold(1, (a, b) => a * b);
  print(product); 
}
void main(){
  productWithFold();
}

2.2.Loops Examples
void countToFive() {
  for (int i = 1; i <= 5; i++) {
    print(i);
  }
}
void main(){
  countToFive();
}

void printNames() {
  List<String> names = ['Ali', 'Leyla', 'Nihad'];
  names.forEach((name) {
    print('Hello, $name');
  });
}
void main(){
  printNames();
  
}

void countdown() {
  int n = 3;
  while (n > 0) {
    print(n);
    n--;
  }
  print('Go!');
}
void main(){
  countdown();
}

2.3🧠 Higher-Order Functions
void main(){
   testApplyFunction();
}
void applyFunction(List<int> list, int Function(int) action) {
  var result = list.map(action).toList();
  print(result);
}

int square(int x) => x * x;

void testApplyFunction() {
  applyFunction([1, 2, 3], square); 
}


void main(){
  useMultiplier();
}
Function makeMultiplier(int factor) {
  return (int x) => x * factor;
}

void useMultiplier() {
  var triple = makeMultiplier(3);
  print(triple(5)); 
}


3.1. Sort a list in ascending or descending order using an optional named parameter
List<int> sortList(List<int> nums, {bool descending = false}) {
  nums.sort();
  if (descending) {
    nums = nums.reversed.toList();
  }
  return nums;
}
 void main(){
   var numsSorted = [3, 1, 4, 2];
  print(sortList(numsSorted)); 
  print(sortList(numsSorted, descending: true));
}
3.2.Keep only even numbers, double them, then sum up the results.
int sumEvenDoubled(List<int> nums) {
  var filtered = nums.where((n) => n % 2 == 0);
  var doubled = filtered.map((n) => n * 2);
  return doubled.reduce((a, b) => a + b);
}
void main() {
  var nums = [1, 2, 3, 4, 5, 6];
  print(sumEvenDoubled(nums));
}

class Person {
 
  String name = 'Asim';
 int age = 10;


  void greet() {
    print("Hello, $name");
  }
}
void main(){
    var student= Person();
    student.greet();
  }



const double xOrigin = 0;
const double yOrigin = 0;

class Point {
  final double x;
  final double y;


  static const Point immutable = const Point(10, 0);

 
  const Point(this.x, this.y);

 
  Point.origin({required double newX, required double newY})
    : x = newX,
      y = newY;
}
 void main(){
     var point = Point.origin(newX: 0.5, newY: 0);
  print(Point.immutable.x);
  print(point.x);
}


abstract class Vehicle {
  void start();

  final int weight;

  Vehicle({required this.weight});
}

class Bike extends Vehicle {
  Bike({required super.weight});

  @override
  void start() {
    print('rolling into deep');
  }
}

class CarWithImpl implements Vehicle {
  @override
  void start() {
   
  }

  @override
  int get weight => throw UnimplementedError();
}

abstract class Animal {
  void makeSound(); 
}


abstract class Payment {
  double amount;
  
  Payment(this.amount);

  void processPayment(); 
}

class CreditCardPayment extends Payment {
  String cardNumber;

  CreditCardPayment(double amount, this.cardNumber) : super(amount);

  @override
  void processPayment() {
    print("Processing Credit Card payment of \$${amount} using card $cardNumber");
  }
}

class PayPalPayment extends Payment {
  String email;

  PayPalPayment(double amount, this.email) : super(amount);

  @override
  void processPayment() {
    print("Processing PayPal payment of \$${amount} from $email");
  }
}

void main() {
  var creditCardPay = CreditCardPayment(110, '416973880000000');
  var payPalPay = PayPalPayment(110, 'myacc@asoiu.edu.az');

  creditCardPay.processPayment();
  payPalPay.processPayment();

}

mixin CanFly {
  void fly() {
    print("Flying...");
  }
}

class User with AgeCalculation {
  final int birthYear;

  User(this.birthYear);

  void calculateAndPrint() {
    print(calculateAge(birthYear));
  }
}

mixin AgeCalculation {
  int calculateAge(int yearOfBirth) {
    int currYear = 2025;
    return currYear - yearOfBirth;
  }
}

class Jet with CanFly {
  void printD() {
    fly();
  }
}

class Bird extends Animal with CanFly {
  @override
  void makeSound() {
    fly();

    print("Chirp Chirp ");
  }
}/*

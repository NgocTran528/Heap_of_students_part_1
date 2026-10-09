``` mermaid
classDiagram
direction TB
    class Address {
        # string street
        # string city
        # string state
        # string zip
        + Address()
        + void init(street, city, state, zip)
        + void printAddress()
    }

    class Date {
        # string dateString
        # int month
        # int day
        # int month
        # int year
        + Date()
        + void init(dateString)
        + void printDate()
    }

    class Student {
        # string studentString
        # string firstName
        # string lastName
        # Date* dob
        # Date* expectedGrad
        # Address* address
        # int creditHours
        + Student()
        + ~Student()
        + void init(studentString)
        + void printStudent()
        + string getFirstName()
        + string getLastName()
        + int getCreditHours()
        + string getLastFirst()
    }

    Address --o Student
    Date --o Student


## Algorithms

### Address:init
```
void init(string street, string city, string state, string zip)
    copy each parameter into the matching data member
```

### Address::printAddress
```
void printAddress()
    print street then a new line
    print city, space, state, comma, space, zip, then a new line
```

### Date::init
```
void init(string dateString)
    save dateString in the data member
    make a stringstream called ss and put dateString in it
    make temporary strings monthStr, dayStr, yearStr
    getline from ss up to '/'into monthStr
    getline from ss up to '/' into dayStr
    getline from ss to the end into yearStr
    use a converter stringstream to turn each one into an int
    store them in month, day, year
```

### Address::printAddress
```
void printAddress()
    print street then a new line
    print city, space, state, comma, space, zip, then a new line
```

### Date::printDate
```
void  printDate()
    make an array of the 12 month names
    print the month name at month -1, space, day, comma, space, year
    print a new line
```

### Student::Student
```
Student()
    make a new Date on the heap for dob
    make a new Date on the heap for expectedGrad
    make a new Address on the heap for address
    set creditHours to 0
```

### Student::~Student
```
~Student()
    delete dob
    delete expectedGrad
    delete address
```

### Student::init
```
void init(string studentString)
    save studentString in the data member
    make a stringstream called splitter and put studentString in it
    getline up to ',' into firstName
    getline up to ',' into lastName
    getline up to ',' into street, city, state, zip
    getine up to ',' into dobStr, gradStr
    getline to the end into creditStr
    call address->init with dobStr
    call expectedGrad-> init with gradStr
    use a converter stringstream to turn creditStr into creditHours
```

### Student::printStudent
```
void printStudent()
    print firstName, space, lastName, new line
    call address->printAddress
    print "DOB: " then call dob->printDate
    print "Grad: " then call expectedGrad->printDate
    print "Credits: " and creditHours, new line
    print a line of underscores
```

### Student::getLastFirst
```
string getLastFirst()
    return lastName + ", " + firstName
```

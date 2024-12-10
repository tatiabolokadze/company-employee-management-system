# კომპანიის თანამშრომლების მართვის სისტემა

## მიზანი

შექმენით კომპანიის თანამშრომლების მართვის სისტემა, რომელიც იყენებს მემკვიდრეობას და პოლიმორფიზმს სხვადასხვა ტიპის თანამშრომლების და მათი ანაზღაურების წარმოსადგენად.

- **`CalculatePay()`** (ვირტუალური მეთოდი, რომელიც აბრუნებს `decimal` ტიპს): ანაზღაურების გამოთვლა
- **`DisplayInfo()`** (ვირტუალური მეთოდი): თანამშრომლის ინფორმაციის ჩვენება

## მემკვიდრე კლასები

შექმენით სამი მემკვიდრე კლასი: `SalariedEmployee`, `HourlyEmployee` და `CommissionEmployee`.

### 1. საბაზო კლასი `Employee`

შექმენით საბაზო კლასი `Employee`, რომელიც შეიცავს შემდეგ ელემენტებს:

- **თვისებები**:
  - `Id` (int): თანამშრომლის უნიკალური იდენტიფიკატორი
  - `Name` (string): თანამშრომლის სახელი
  - `HireDate` (DateTime): თანამშრომლის დაქირავების თარიღი

- **მეთოდები**:
  - `CalculatePay()`: ვირტუალური მეთოდი, რომელიც გამოთვლის თანამშრომლის ანაზღაურებას (ეს უნდა გადაფაროს მემკვიდრე კლასებში).
  - `DisplayInfo()`: ვირტუალური მეთოდი, რომელიც აჩვენებს თანამშრომლის ინფორმაციას (ასევე გადაფარავს მემკვიდრე კლასებში).

### 2. მემკვიდრე კლასები

#### 2.1 `SalariedEmployee`

- **დამატებითი თვისება**:
  - `AnnualSalary` (decimal): წლიური ხელფასი

- **მეთოდები**:
  - გადაფარეთ `CalculatePay()` მეთოდი: დააბრუნეთ თვიური ხელფასი (წლიური ხელფასი გაყოფილი 12-ზე).
  - გადაფარეთ `DisplayInfo()` მეთოდი: დაამატეთ წლიური ხელფასის ინფორმაცია.

#### 2.2 `HourlyEmployee`

- **დამატებითი თვისებები**:
  - `HourlyRate` (decimal): საათობრივი ანაზღაურება
  - `HoursWorked` (decimal): ნამუშევარი საათები

- **მეთოდები**:
  - გადაფარეთ `CalculatePay()` მეთოდი: დააბრუნეთ ნამუშევარი საათები გამრავლებული საათობრივ ანაზღაურებაზე.
  - გადაფარეთ `DisplayInfo()` მეთოდი: დაამატეთ საათობრივი ანაზღაურებისა და ნამუშევარი საათების ინფორმაცია.

#### 2.3 `CommissionEmployee`

- **დამატებითი თვისებები**:
  - `BaseSalary` (decimal): ძირითადი ხელფასი
  - `CommissionRate` (decimal): საკომისიოს პროცენტი (0-დან 1-მდე)
  - `SalesAmount` (decimal): გაყიდვების რაოდენობა

- **მეთოდები**:
  - გადაფარეთ `CalculatePay()` მეთოდი: დააბრუნეთ ძირითადი ხელფასი პლუს (გაყიდვების რაოდენობა გამრავლებული საკომისიოს პროცენტზე).
  - გადაფარეთ `DisplayInfo()` მეთოდი: დაამატეთ ძირითადი ხელფასის, საკომისიოს პროცენტისა და გაყიდვების რაოდენობის ინფორმაცია.

### 3. `Department` კლასი

შექმენით `Department` კლასი, რომელიც მართავს თანამშრომლებს:

- **თვისებები**:
  - `Name` (string): დეპარტამენტის სახელი
  - `Employees` (List<Employee>): თანამშრომლების სია

- **მეთოდები**:
  - `AddEmployee(Employee employee)`: თანამშრომლის დამატება დეპარტამენტში
  - `RemoveEmployee(int employeeId)`: თანამშრომლის წაშლა დეპარტამენტიდან ID-ის მიხედვით
  - `DisplayAllEmployees()`: დეპარტამენტის ყველა თანამშრომლის ინფორმაციის ჩვენება
  - `CalculateDepartmentPayroll()`: დეპარტამენტის მთლიანი სახელფასო ფონდის გამოთვლა

### 4. `Company` კლასი

შექმენით `Company` კლასი, რომელიც მართავს დეპარტამენტებს:

- **თვისებები**:
  - `Name` (string): კომპანიის სახელი
  - `Departments` (List<Department>): დეპარტამენტების სია

- **მეთოდები**:
  - `AddDepartment(Department department)`: დეპარტამენტის დამატება
  - `RemoveDepartment(string departmentName)`: დეპარტამენტის წაშლა სახელის მიხედვით
  - `DisplayAllDepartments()`: ყველა დეპარტამენტის ინფორმაციის გამოჩენა
  - `CalculateTotalPayroll()`: კომპანიის მთლიანი სახელფასო ფონდის გამოთვლა

---

## განმარტება

ეს დავალება აჩვენებს, როგორ შეიძლება გამოვიყენოთ მემკვიდრეობა და პოლიმორფიზმი რთული ბიზნეს სისტემის მოდელირებისთვის. `Employee` კლასი არის საბაზო კლასი, რომელიც განსაზღვრავს საერთო თვისებებს და ქცევას ყველა თანამშრომლისთვის. მემკვიდრე კლასები (`SalariedEmployee`, `HourlyEmployee`, `CommissionEmployee`) კონკრეტულ ტიპებს ასახავს და მათთვის შესაბამისი ქცევას განსაზღვრავს. 

`Department` და `Company` კლასები აჩვენებენ, როგორ შეიძლება ორგანიზაციული სტრუქტურის მოდელირება. ისინი იყენებენ პოლიმორფიზმს, რათა ერთნაირად მოეპყრან სხვადასხვა ტიპის თანამშრომლებს, მაგალითად, ხელფასის გამოთვლისას.

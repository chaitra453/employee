# employee
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Employee Management System</title>
    <style>
        body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #e48888;
}

.container {
    max-width: 800px;
    margin: 20px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    margin-bottom: 20px;
    color: #333;
}

button {
    display: block;
    width: 100%;
    padding: 10px 15px;
    margin-bottom: 10px;
    background-color: #e51a17;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

button:hover {
    background-color: #8c3629;
}

#output {
    margin-bottom: 20px;
}

    </style>
</head>
<body>
    <div class="container">
        <h1>Employee Management System</h1>
        <div id="output"></div>
        <button onclick="calculateAverageSalary()">Calculate Average Salary</button>
        <button onclick="findEmployeesByDepartment('Marketing')">Find Employees in Marketing</button>
        <button onclick="increaseSalary(10)">Increase Salaries by 10%</button>
        <button onclick="sortEmployeesByAge()">Sort Employees by Age</button>
    </div>

<script>
    function Employee(name, age, department, salary) {
    this.name = name;
    this.age = age;
    this.department = department;
    this.salary = salary;
}

let employees = [
    new Employee("John", 30, "Marketing", 50000),
    new Employee("Alice", 35, "HR", 60000),
    new Employee("Bob", 28, "IT", 70000),
    new Employee("Emily", 32, "Marketing", 55000)
];

function displayOutput(output) {
    document.getElementById('output').innerHTML = output;
}

function calculateAverageSalary() {
    let totalSalary = employees.reduce((acc, emp) => acc + emp.salary, 0);
    let averageSalary = totalSalary / employees.length;
    displayOutput(`Average Salary: $${averageSalary.toFixed(2)}`);
}

function findEmployeesByDepartment(department) {
    let filteredEmployees = employees.filter(emp => emp.department === department);
    displayOutput(`Employees in ${department}: ${filteredEmployees.map(emp => emp.name).join(', ')}`);
}

function increaseSalary(percentage) {
    employees.forEach(emp => {
        emp.salary += emp.salary * (percentage / 100);
    });
    displayOutput('Salaries increased successfully!');
}

function sortEmployeesByAge() {
    employees.sort((a, b) => a.age - b.age);
    displayOutput(`Employees Sorted by Age: ${employees.map(emp => emp.name).join(', ')}`);
}

</script></body>
</html>

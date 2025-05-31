<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>🇮🇳 Student Registration - CRUD App</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>📘 Student Registration Form 🇮🇳</h1>
    
    <form id="studentForm">
      <div class="form-group">
        <input type="text" id="fullName" required />
        <label for="fullName">👤 Full Name</label>
      </div>

      <div class="form-group">
        <input type="email" id="email" required />
        <label for="email">📧 Email</label>
      </div>

      <div class="form-group">
        <input type="tel" id="phone" required />
        <label for="phone">📱 Phone Number</label>
      </div>

      <div class="form-group">
        <input type="number" id="age" required />
        <label for="age">🎂 Age</label>
      </div>

      <div class="form-group">
        <input type="text" id="course" required />
        <label for="course">📘 Course</label>
      </div>

      <div class="form-group">
        <input type="text" id="enroll" required />
        <label for="enroll">🎓 Enrollment No.</label>
      </div>

      <button type="submit">➕ Add Student</button>
    </form>

    <div id="studentList">
      <!-- Pre-filled records will go here -->
    </div>
  </div>
  <link rel="stylesheet" href="style.css">


  <script src="script.js"></script>
</body>
</html>
/* style.css */
body {
  font-family: 'Segoe UI', sans-serif;
  background: #fff8e1;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 800px;
  margin: 50px auto;
  padding: 20px;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #e65100;
  margin-bottom: 20px;
}

form {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.form-group {
  position: relative;
  flex: 1 1 45%;
}

input {
  width: 100%;
  padding: 12px 10px;
  font-size: 16px;
  border: 2px solid #ff9800;
  border-radius: 6px;
  outline: none;
  background: transparent;
}

label {
  position: absolute;
  left: 12px;
  top: 12px;
  background-color: #fff8e1;
  color: #999;
  transition: all 0.3s ease;
  padding: 0 5px;
  pointer-events: none;
}

input:focus + label,
input:not(:placeholder-shown):valid + label {
  top: -8px;
  left: 8px;
  font-size: 12px;
  color: #e65100;
  background: #fff8e1;
}

button {
  width: 100%;
  padding: 12px;
  background-color: #ff5722;
  color: white;
  font-size: 18px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background-color: #e64a19;
}
// script.js
const studentForm = document.getElementById("studentForm");
const studentList = document.getElementById("studentList");

let students = [
  {
    fullName: "Aryan Sharma",
    email: "aryan@gmail.com",
    phone: "9876543210",
    age: 20,
    course: "B.Tech",
    enroll: "ECE2025IND001"
  },
  {
    fullName: "Sneha Patel",
    email: "sneha@gmail.com",
    phone: "9090909090",
    age: 19,
    course: "B.Sc",
    enroll: "BIO2025IND002"
  },
  {
    fullName: "Ravi Kumar",
    email: "ravi@gmail.com",
    phone: "9812345678",
    age: 21,
    course: "B.Com",
    enroll: "COM2025IND003"
  },
  {
    fullName: "Aarti Verma",
    email: "aarti@gmail.com",
    phone: "9123456789",
    age: 22,
    course: "B.A",
    enroll: "ART2025IND004"
  },
  {
    fullName: "Karan Singh",
    email: "karan@gmail.com",
    phone: "7001234567",
    age: 23,
    course: "M.Tech",
    enroll: "CSE2025IND005"
  }
];

function displayStudents() {
  studentList.innerHTML = students.map((stu, index) => `
    <div class="student-card">
      <h3>👨‍🎓 ${stu.fullName}</h3>
      <p>📧 ${stu.email}</p>
      <p>📱 ${stu.phone}</p>
      <p>🎓 ${stu.course} | 🆔 ${stu.enroll}</p>
      <button onclick="editStudent(${index})">✏️ Edit</button>
      <button onclick="deleteStudent(${index})">🗑️ Delete</button>
    </div>
  `).join("");
}

studentForm.addEventListener("submit", function (e) {
  e.preventDefault();
  const newStudent = {
    fullName: document.getElementById("fullName").value,
    email: document.getElementById("email").value,
    phone: document.getElementById("phone").value,
    age: document.getElementById("age").value,
    course: document.getElementById("course").value,
    enroll: document.getElementById("enroll").value
  };
  students.push(newStudent);
  displayStudents();
  studentForm.reset();
});

function deleteStudent(index) {
  students.splice(index, 1);
  displayStudents();
}

function editStudent(index) {
  const stu = students[index];
  document.getElementById("fullName").value = stu.fullName;
  document.getElementById("email").value = stu.email;
  document.getElementById("phone").value = stu.phone;
  document.getElementById("age").value = stu.age;
  document.getElementById("course").value = stu.course;
  document.getElementById("enroll").value = stu.enroll;
  students.splice(index, 1);
}

displayStudents();


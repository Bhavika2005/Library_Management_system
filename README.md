# Library_Management_system
This project is a Library Management System designed to manage student registration, login, book addition, book issuing, and book viewing in a simple digital environment.  It works as a mini online library where students can register, log in, and interact with library resources through different pages.
#register_page
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Register</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: url('background2.jpeg') no-repeat center center/cover;
        }
        
        .container {
            width: 350px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
            text-align: center;
            color: white;
        }
        
        h2 {
            margin-bottom: 20px;
        }
        
        input {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            border: none;
            border-radius: 8px;
            outline: none;
        }
        
        button {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border: none;
            border-radius: 8px;
            background: #00c6ff;
            color: white;
            font-size: 16px;
            cursor: pointer;
        }
        
        button:hover {
            background: #0072ff;
        }
        
        a {
            color: #00c6ff;
            text-decoration: none;
        }
        
        p {
            margin-top: 15px;
        }
    </style>
</head>

<body>

    <div class="container">

        <h2>📚 Student Registration</h2>

        <form onsubmit="registerUser(event)">

            <input type="text" id="name" placeholder="Full Name" required>

            <input type="email" id="email" placeholder="Email" required>

            <input type="text" id="username" placeholder="Username" required>

            <input type="password" id="password" placeholder="Password" required>

            <button type="submit">Register</button>

        </form>

        <p>Already registered? <a href="login.html">Login</a></p>

    </div>

    <script>
        function registerUser(event) {
            event.preventDefault();

            let student = {
                name: document.getElementById("name").value,
                email: document.getElementById("email").value,
                username: document.getElementById("username").value,
                password: document.getElementById("password").value
            };

            localStorage.setItem("student", JSON.stringify(student));

            alert("Registration Successful!");

            window.location.href = "login.html";
        }
    </script>

Login_page
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Login</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: url('background2.jpeg') no-repeat center center/cover;
        }
        
        .container {
            position: relative;
            width: 350px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
            text-align: center;
            color: white;
        }
        
        h2 {
            margin-bottom: 20px;
        }
        
        input {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            border: none;
            border-radius: 8px;
            outline: none;
        }
        
        button {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border: none;
            border-radius: 8px;
            background: #00c6ff;
            color: white;
            font-size: 16px;
            cursor: pointer;
        }
        
        button:hover {
            background: #0072ff;
        }
        
        a {
            color: #00c6ff;
            text-decoration: none;
        }
        
        p {
            margin-top: 15px;
        }
    </style>
</head>

<body>

    <div class="container">

        <h2>🔐 Student Login</h2>

        <form onsubmit="loginUser(event)">

            <input type="text" id="username" placeholder="Username" required>

            <input type="password" id="password" placeholder="Password" required>

            <button type="submit">Login</button>

        </form>

        <p>New student? <a href="register.html">Register</a></p>

    </div>

    <script>
        function loginUser(event) {
            event.preventDefault();

            let storedStudent = JSON.parse(localStorage.getItem("student"));

            let username = document.getElementById("username").value;
            let password = document.getElementById("password").value;

            if (!storedStudent) {
                alert("No student registered! Please register first.");
                return;
            }

            if (username === storedStudent.username && password === storedStudent.password) {
                alert("Login Successful!");
                window.location.href = "dashboard.html";
            } else {
                alert("Invalid Username or Password!");
            }
        }
    </script>

</body>

</html>

Dashboard_page
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Dashboard</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: url('background2.jpeg') no-repeat center center/cover;
        }
        
        body::before {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
        }
        
        .container {
            position: relative;
            width: 500px;
            padding: 35px;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            border-radius: 15px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
            text-align: center;
            color: white;
        }
        
        h1 {
            margin-bottom: 15px;
        }
        
        h3 {
            margin-bottom: 25px;
            color: #ddd;
        }
        
        .btn {
            display: block;
            width: 100%;
            padding: 14px;
            margin: 10px 0;
            border: none;
            border-radius: 8px;
            background: #00c6ff;
            color: white;
            font-size: 16px;
            cursor: pointer;
            text-decoration: none;
        }
        
        .btn:hover {
            background: #0072ff;
        }
        
        .logout {
            background: crimson;
        }
        
        .logout:hover {
            background: darkred;
        }
    </style>
</head>

<body>

    <div class="container">

        <h1>📚 Library Dashboard</h1>

        <h3 id="welcome"></h3>

        <p id="totalBooks"></p>

        <p id="totalIssued"></p>

        <a href="add_book.html" class="btn">➕ Add Books</a>

        <a href="issue_book.html" class="btn">📖 Issue Books</a>

        <button class="btn logout" onclick="logoutUser()">🚪 Logout</button>

    </div>

    <script>
        let student = JSON.parse(localStorage.getItem("student"));

        if (!student) {
            alert("Please login first!");
            window.location.href = "login.html";
        } else {
            document.getElementById("welcome").innerText =
                "Welcome, " + student.name + " (" + student.username + ")";
        }

        /* ALL BOOKS IN LIBRARY */
        let books = JSON.parse(localStorage.getItem("books")) || [];

        /* ONLY CURRENT USER'S ISSUED BOOKS */
        let userIssuedBooks =
            JSON.parse(localStorage.getItem("issuedBooks_" + student.username)) || [];

        /* SHOW DATA */
        document.getElementById("totalBooks").innerText =
            "📚 Total Books Available: " + books.length;

        document.getElementById("totalIssued").innerText =
            "📖 Your Issued Books: " + userIssuedBooks.length;

        /* LOGOUT */
        function logoutUser() {
            localStorage.removeItem("student");
            alert("Logged out successfully!");
            window.location.href = "login.html";
        }
    </script>

</body>

</html>

Add_books_page
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Add Book</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: url('background2.jpeg') no-repeat center center/cover;
        }
        
        body::before {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
        }
        
        .container {
            position: relative;
            width: 400px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            border-radius: 15px;
            text-align: center;
            color: white;
        }
        
        h2 {
            margin-bottom: 20px;
        }
        
        input {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            border: none;
            border-radius: 8px;
            outline: none;
        }
        
        button,
        .back-btn {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border: none;
            border-radius: 8px;
            background: #00c6ff;
            color: white;
            font-size: 16px;
            cursor: pointer;
            text-decoration: none;
            display: block;
        }
        
        button:hover,
        .back-btn:hover {
            background: #0072ff;
        }
    </style>
</head>

<body>

    <div class="container">

        <h2>➕ Add New Book</h2>

        <form onsubmit="addBook(event)">

            <input type="text" id="bookName" placeholder="Book Name" required>

            <input type="text" id="author" placeholder="Author Name" required>

            <input type="text" id="category" placeholder="Category" required>

            <input type="number" id="quantity" placeholder="Quantity" required>

            <button type="submit">Add Book</button>

        </form>

        <a href="dashboard.html" class="back-btn">⬅ Back to Dashboard</a>

    </div>

    <script>
        function addBook(event) {
            event.preventDefault();

            let book = {
                bookName: document.getElementById("bookName").value,
                author: document.getElementById("author").value,
                category: document.getElementById("category").value,
                quantity: document.getElementById("quantity").value
            };

            let books = JSON.parse(localStorage.getItem("books")) || [];

            books.push(book);

            localStorage.setItem("books", JSON.stringify(books));

            alert("Book Added Successfully!");

            window.location.href = "dashboard.html";
        }
    </script>

</body>

</html>

Issue_book_page
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Issue Book</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: url('background2.jpeg') no-repeat center center/cover;
        }
        
        body::before {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
        }
        
        .container {
            position: relative;
            width: 400px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            border-radius: 15px;
            text-align: center;
            color: white;
        }
        
        h2 {
            margin-bottom: 20px;
        }
        
        input {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            border: none;
            border-radius: 8px;
            outline: none;
        }
        
        button,
        .back-btn {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border: none;
            border-radius: 8px;
            background: #00c6ff;
            color: white;
            font-size: 16px;
            cursor: pointer;
            text-decoration: none;
            display: block;
        }
        
        button:hover,
        .back-btn:hover {
            background: #0072ff;
        }
    </style>
</head>

<body>

    <div class="container">

        <h2>📖 Issue Book</h2>

        <form onsubmit="issueBook(event)">

            <input type="text" id="studentName" placeholder="Student Name" required>

            <input type="text" id="bookName" placeholder="Book Name" required>

            <input type="date" id="issueDate" required>

            <input type="date" id="returnDate" required>

            <button type="submit">Issue Book</button>

        </form>

        <a href="dashboard.html" class="back-btn">⬅ Back to Dashboard</a>

    </div>

    <script>
        function issueBook(event) {
            event.preventDefault();

            let issuedBook = {
                studentName: document.getElementById("studentName").value,
                bookName: document.getElementById("bookName").value,
                issueDate: document.getElementById("issueDate").value,
                returnDate: document.getElementById("returnDate").value
            };

            let issuedBooks = JSON.parse(localStorage.getItem("issuedBooks")) || [];

            issuedBooks.push(issuedBook);

            localStorage.setItem("issuedBooks", JSON.stringify(issuedBooks));

            alert("Book Issued Successfully!");

            window.location.href = "dashboard.html";
        }
    </script>

</body>

</html>

View_books_page
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>View Books</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            min-height: 100vh;
            padding: 30px;
            background: url('background2.jpeg') no-repeat center center/cover;
            color: white;
        }
        
        body::before {
            content: "";
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.6);
            z-index: -1;
        }
        
        h1 {
            text-align: center;
            margin-bottom: 30px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(10px);
            border-radius: 10px;
            overflow: hidden;
        }
        
        th,
        td {
            padding: 15px;
            text-align: center;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        th {
            background: rgba(0, 198, 255, 0.3);
        }
        
        tr:hover {
            background: rgba(255, 255, 255, 0.1);
        }
        
        .btn {
            display: inline-block;
            margin-top: 20px;
            padding: 12px 20px;
            background: #00c6ff;
            color: white;
            text-decoration: none;
            border-radius: 8px;
        }
        
        .btn:hover {
            background: #0072ff;
        }
    </style>
</head>

<body>

    <h1>📚 Library Book Collection</h1>

    <table>
        <thead>
            <tr>
                <th>#</th>
                <th>Book Name</th>
                <th>Author</th>
                <th>Category</th>
                <th>Quantity</th>
            </tr>
        </thead>

        <tbody id="bookList">
        </tbody>
    </table>

    <div style="text-align:center;">
        <a href="dashboard.html" class="btn">⬅ Back to Dashboard</a>
    </div>

    <script>
        let books = JSON.parse(localStorage.getItem("books")) || [];

        let bookList = document.getElementById("bookList");

        if (books.length === 0) {
            bookList.innerHTML = `
        <tr>
            <td colspan="5">No books added yet.</td>
        </tr>
    `;
        } else {
            books.forEach((book, index) => {
                bookList.innerHTML += `
            <tr>
                <td>${index + 1}</td>
                <td>${book.bookName}</td>
                <td>${book.author}</td>
                <td>${book.category}</td>
                <td>${book.quantity}</td>
            </tr>
        `;
            });
        }
    </script>

</body>

</html>
</body>

</html>

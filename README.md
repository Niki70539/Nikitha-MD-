# Nikitha-MD-
Build user management dashboard 
Create a web application featuring a user management dashboard with two tabs: User Details and Account Creation. The User Details tab will display user information fetched from a database in a searchable table format, allowing users to search for specific entries. The Account Creation tab will consist of a form for username and password input.
Requirements:

User Details Tab:

Fetch user data from a placeholder database.
Implement a searchable table displaying user information: Username, Email, Phone, ID, and Creation date.
Enable a click action on any user in the search results to open a popup/modal with a button to generate a report for the selected user.
Account Creation Tab:

Create a form with fields for username and password.
Implement dummy request handling upon form submission.
Dashboard Interface:

Design a clean and intuitive dashboard layout with two tabs: User Details and Account Creation.
Tech Stack:

Use either React or Vue.js for frontend development (Vue.js is preferred).
Implement styling using CSS/SCSS/SASS or Tailwind CSS (Tailwind CSS is preferred) without relying on any component libraries.
Optional but preferred: Use SSR (Server-Side Rendering) with Next.js or Nuxt.js.
Aim for a high Lighthouse score, striving for a score between 90 and 100 to optimize user experience.

HTML and CSS code for a User Management Dashboard with two tabs: User Details and Account Creation:

HTML:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Management Dashboard</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>User Management Dashboard</h1>

        <div class="tabs">
            <button class="tab-link active" data-tab="user-details">User Details</button>
            <button class="tab-link" data-tab="account-creation">Account Creation</button>
        </div>

        <div class="tab-content">
            <div class="tab-pane active" id="user-details">
                <h2>User Details</h2>

                <input type="text" placeholder="Search by username or email" id="user-search">

                <table>
                    <thead>
                        <tr>
                            <th>Username</th>
                            <th>Email</th>
                            <th>Phone</th>
                            <th>ID</th>
                            <th>Creation Date</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>user1</td>
                            <td>user1@example.com</td>
                            <td>+1234567890</td>
                            <td>1</td>
                            <td>2023-10-04</td>
                        </tr>
                        <tr>
                            <td>user2</td>
                            <td>user2@example.com</td>
                            <td>+9876543210</td>
                            <td>2</td>
                            <td>2023-10-05</td>
                        </tr>
                        <tr>
                            <td>user3</td>
                            <td>user3@example.com</td>
                            <td>+1234567890</td>
                            <td>3</td>
                            <td>2023-10-06</td>
                        </tr>
                    </tbody>
                </table>

                <div class="popup" id="user-report-popup">
                    <div class="popup-content">
                        <h2>User Report</h2>
                        <p>Report content will be displayed here.</p>

                        <button class="popup-close">Close</button>
                    </div>
                </div>
            </div>

            <div class="tab-pane" id="account-creation">
                <h2>Account Creation</h2>

                <form id="account-creation-form">
                    <label for="username">Username:</label>
                    <input type="text" id="username" name="username" required>

                    <label for="password">Password:</label>
                    <input type="password" id="password" name="password" required>

                    <button type="submit">Create Account</button>
                </form>
            </div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>

 CSS

body {
    font-family: sans-serif;
}

.container {
    width: 800px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
}

h1 {
    text-align: center;
    margin-bottom: 20px;
}

.tabs {
    display: flex;
    justify-content: center;
}

.tab-link {
    padding: 10px;
    border: 1px solid #ccc;
    margin-right: 10px;
    cursor: pointer;
}

.tab-link.active {
    background-color: #eee;
}

.tab-content {
    margin-top: 20px;
}

.tab-pane {
    display: none;
}

.tab-pane.active {
    display: block;
}

table {
    width: 100%;
    border-collapse: collapse;
}

th, td {
    padding: 5px;
    border: 1px solid #ccc;
}

#user-search {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    margin-bottom

1   User Details Tab

Fetch user data from a placeholder database.

<script setup>
import axios from 'axios';

const url = 'https://jsonplaceholder.typicode.com/users';

const users = await axios.get(url);

const filteredUsers = ref([]);

const searchTerm = ref('');

watch(searchTerm, (val) => {
  filteredUsers.value = users.data.filter((user) => {
    return user.username.toLowerCase().includes(val.toLowerCase());
  });
});
</script>

<template>
  <div class="flex flex-col">
    <input type="text" v-model="searchTerm" placeholder="Search users" class="mb-4" />

    <table class="table-auto w-full">
      <thead>
        <tr>
          <th>Username</th>
          <th>Email</th>
          <th>Phone</th>
          <th>ID</th>
          <th>Creation Date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in filteredUsers" :key="user.id" @click="openReportModal(user)">
          <td>{{ user.username }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.phone }}</td>
          <td>{{ user.id }}</td>
          <td>{{ user.createdAt }}</td>
        </tr>
      </tbody>
    </table>
  </div>

  <ReportModal :user="selectedUser" />
</template>

2  Implement a searchable table displaying user information: Username, Email, Phone, ID, and Creation date.

CSS

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

3  Enable a click action on any user in the search results to open a popup/modal with a button to generate a report for the selected user.

<script setup>
import ReportModal from './ReportModal.vue';

const selectedUser = ref(null);

const openReportModal = (user) => {
  selectedUser.value = user;
};
</script>

**Account Creation Tab**

1  Create a form with fields for username and password.

<template>
  <div class="flex flex-col">
    <input type="text" placeholder="Username" class="mb-4" />
    <input type="password" placeholder="Password" class="mb-4" />

    <button type="submit" class="bg-blue-500 text-white py-2 px-4 rounded">Create Account</button>
  </div>
</template>


2 Implement dummy request handling upon form submission

<script setup>
const handleSubmit = () => {
  // Simulate API call
  console.log('Creating new account...');
};
</script>

**Dashboard Interface**

1  Design a clean and intuitive dashboard layout with two tabs: User Details and Account Creation.

CSS


.dashboard {
  display: flex;
  height: 100vh;
}

.sidebar {
  width: 200px;
  background-color: #f2f2f2;
  padding: 20px;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar li {
  margin-bottom: 10px;
}

.sidebar li a {
  text-decoration: none;
  color: #000;
}

.sidebar li a:hover {
  text-decoration: underline;
}

.main-content {
  flex: 1;
  padding: 20px;
}

HTML

<div class="dashboard">
  <div class="sidebar">
    <ul>
      <li><a href="#">User Details</a></li>
      <li><a href="#">Account Creation</a></li>
    </ul>
  </div>



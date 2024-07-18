# java-script-assignment
Aim:To Create a fully functional To-Do-List application using ES6 JavaScript.
# Program:
# html:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="Javascript Assignment.css">
</head>
<body>
    <div class="container">
        <h1>Work To-Dos</h1>
        <p>Enter text into the input field to add items to your list.</p>
        <p>Click the item to mark it as complete.</p>
        <p>Click the "X" to remove the item from your list.</p>
        <form id="task-form">
            <input type="text" id="task-title" placeholder="New item...">
            <input type="text" id="task-desc" placeholder="Description...">
            <input type="date" id="task-date">
            <button type="submit">Add Task</button>
        </form>
        <ul id="task-list"></ul>
    </div>
    <script type="module" src="js.js"></script>
</body>
</html>
```
# css:
```
body {
    font-family: Arial, sans-serif;
    background-color: #fdfd06;
    color: #ffffff;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background: #ffffff;
    border-radius: 8px;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
    color: #333333;
    max-width: 500px;
    width: 100%;
}

form {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

form input, form button {
    padding: 10px;
    margin: 5px 0;
}
ul {
    list-style: none;
    padding: 0;
}

li {
    background: #f9f9f9;
    margin: 5px 0;
    padding: 10px;
    border-radius: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

li.completed {
    text-decoration: line-through;
    color: #999999;
}

li button {
    background: #ff4444;
    border: none;
    color: #ffffff;
    padding: 5px 10px;
    border-radius: 4px;
    cursor: pointer;
}

li button:hover {
    background: #ff2222;
}
```
# javascript1:
```
import Task from './Task.js';

export default class ToDoList {
    constructor() {
        this.tasks = JSON.parse(localStorage.getItem('tasks')) || [];
    }

    addTask(task) {
        this.tasks.push(task);
        this.saveTasks();
    }

    editTask(index, updatedTask) {
        this.tasks[index] = updatedTask;
        this.saveTasks();
    }

    deleteTask(index) {
        this.tasks.splice(index, 1);
        this.saveTasks();
    }

    toggleTaskCompletion(index) {
        this.tasks[index].completed = !this.tasks[index].completed;
        this.saveTasks();
    }
    filterTasks(filter) {
        return this.tasks.filter(task => {
            if (filter === 'all') return true;
            if (filter === 'completed') return task.completed;
            if (filter === 'incomplete') return !task.completed;
        });
    }

    saveTasks() {
        localStorage.setItem('tasks', JSON.stringify(this.tasks));
    }

    fetchTasksFromAPI(apiEndpoint) {
        fetch(apiEndpoint)
            .then(response => response.json())
            .then(data => {
                this.tasks = data.map(task => new Task(task.title, task.description, task.dueDate, task.completed));
                this.saveTasks();
            });
    }
}
```
# javascript2:
```
import Task from './Task.js';

export default class ToDoList {
    constructor() {
        this.tasks = JSON.parse(localStorage.getItem('tasks')) || [];
    }

    addTask(task) {
        this.tasks.push(task);
        this.saveTasks();
    }

    editTask(index, updatedTask) {
        this.tasks[index] = updatedTask;
        this.saveTasks();
    }

    deleteTask(index) {
        this.tasks.splice(index, 1);
        this.saveTasks();
    }

    toggleTaskCompletion(index) {
        this.tasks[index].completed = !this.tasks[index].completed;
        this.saveTasks();
    }
    filterTasks(filter) {
        return this.tasks.filter(task => {
            if (filter === 'all') return true;
            if (filter === 'completed') return task.completed;
            if (filter === 'incomplete') return !task.completed;
        });
    }

    saveTasks() {
        localStorage.setItem('tasks', JSON.stringify(this.tasks));
    }

    fetchTasksFromAPI(apiEndpoint) {
        fetch(apiEndpoint)
            .then(response => response.json())
            .then(data => {
                this.tasks = data.map(task => new Task(task.title, task.description, task.dueDate, task.completed));
                this.saveTasks();
            });
    }
}
```
# output:
![output](https://github.com/user-attachments/assets/8fd96fc2-c017-4e63-9ddd-50c8fc752235)


# Result:
Thus,fully functional To-Do-List application using ES6 JavaScript was executed successfuly.

# To-Do-list
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple To-Do List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        input[type="text"], button {
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #ddd;
            width: calc(100% - 22px);
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        ul li {
            padding: 10px;
            border-bottom: 1px solid #ddd;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .task-completed {
            text-decoration: line-through;
        }

        button {
            background-color: #5cabff;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            opacity: 0.8;
        }

        .delete-btn {
            background-color: red;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <input type="text" id="taskInput" placeholder="Add a new task...">
        <button onclick="addTask()">Add Task</button>
        <ul id="taskList"></ul>
    </div>

    <script>
        function addTask() {
            const input = document.getElementById('taskInput');
            const newTask = input.value.trim();

            if (newTask) {
                const listItem = document.createElement('li');
                listItem.textContent = newTask;

                const deleteBtn = document.createElement('button');
                deleteBtn.textContent = 'Delete';
                deleteBtn.className = 'delete-btn';
                deleteBtn.onclick = function() { listItem.remove(); };

                const completeBtn = document.createElement('button');
                completeBtn.textContent = 'Complete';
                completeBtn.onclick = function() { listItem.classList.toggle('task-completed'); };

                listItem.appendChild(completeBtn);
                listItem.appendChild(deleteBtn);

                document.getElementById('taskList').appendChild(listItem);
                input.value = ''; // Clear input field
            } else {
                alert('Please enter a task.');
            }
        }
    </script>
</body>
</html>

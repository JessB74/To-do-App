# sv



> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.

Svelte To-Do App
A simple and interactive To-Do List application built with Svelte and SvelteKit. This app allows users to add, complete, and remove tasks with persistent data storage using localStorage.

Features
Add tasks with a user-friendly input field.
Mark tasks as completed or uncompleted.
Remove tasks from the list.
Tasks are saved to localStorage for persistence across page reloads.
Responsive design for various screen sizes.
Project Structure
The app follows the typical SvelteKit structure:
svelte-todo-app/
├── public/                   # Static files
├── src/
│   ├── routes/               # Route files
│   │   ├── +page.svelte      # Main To-Do App component
│   ├── app.css               # Global styles (optional)
│   └── app.html              # Entry HTML
├── svelte.config.js          # Svelte configuration
├── package.json              # Project metadata and dependencies
└── README.md                 # Project documentation

Getting Started
1. Prerequisites
Make sure you have the following installed:

Node.js (16 or higher)
npm (bundled with Node.js)
2. Installation
1.Clone the repository:
git clone https://github.com/your-username/svelte-todo-app.git
cd svelte-todo-app
2.Install dependencies:

npm install
3. Running the Development Server
Start the SvelteKit development server:

npm run dev

4. Building for Production
To create an optimized build for production:
npm run build

5. Deploying
For deployment, choose your platform (e.g., Vercel, Netlify, GitHub Pages) and use the appropriate SvelteKit adapter.

Usage
Adding a Task
Enter a task in the input field.
Press the "Add" button or hit the Enter key.
Marking a Task as Completed
Click on a task to toggle its completion status.
Removing a Task
Click the × button next to a task to remove it from the list.
Code Overview
Main Components
+page.svelte:
Manages task logic, including adding, completing, and removing tasks.
Integrates localStorage for data persistence.
Example Snippet:
<script>
  let tasks = [];
  let input = '';

  function addTask() {
    if (!input.trim()) {
      alert("Please input a task!");
      return;
    }
    tasks = [...tasks, { text: input, completed: false }];
    input = '';
    saveData();
  }

  function saveData() {
    localStorage.setItem("tasks", JSON.stringify(tasks));
  }
</script>

Styling
The app includes responsive styling and is optimized for various devices.

Key CSS Snippet:
.container {
  width: 100%;
  min-height: 100vh;
  background: linear-gradient(135deg, #fbc2eb, #a18cd1, #a6c1ee);
  padding: 10px;
}

.todo-app {
  max-width: 60vw;
  margin: 100px auto;
  padding: 40px;
  background: #fff;
  border-radius: 20px;
}
Tech Stack
Frontend: Svelte, SvelteKit
Styling: CSS with scoped styles
Persistence: LocalStorage

Future Enhancements
Add a feature to edit tasks.
Integrate a backend for multi-user support.
Add drag-and-drop functionality for reordering tasks.
License
This project is licensed under the MIT License.
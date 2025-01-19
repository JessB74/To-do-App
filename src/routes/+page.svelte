<script>
 /*
   * To-Do List Component
   *
   * Features:
   * - Add tasks to a list
   * - Mark tasks as completed
   * - Remove tasks from the list
   * - Persist tasks using localStorage
   *
   * Styling is scoped to this component.
   */





// Reactive variables
let input = ""; // Holds the input value
  let tasks = []; // Holds the list of tasks

  // Add a new task
  function addTask() {
    if (!input.trim()) {
      alert("Please input a task!");
      return;
    }

    // Add the new task to the tasks array
    tasks = [...tasks, { text: input, completed: false }];
    input = ""; // Clear the input field
    saveData(); // Save tasks to localStorage
  }

  // Toggle task completion
  function toggleTask(index) {
    tasks[index].completed = !tasks[index].completed;
    tasks = [...tasks]; // Trigger reactivity
    saveData();
  }

  // Remove a task
  function removeTask(index) {
    tasks = tasks.filter((_, i) => i !== index);
    saveData();
  }

  // Save tasks to localStorage
  function saveData() {
    localStorage.setItem("tasks", JSON.stringify(tasks));
  }

  // Load tasks from localStorage
  function loadData() {
    const savedTasks = localStorage.getItem("tasks");
    tasks = savedTasks ? JSON.parse(savedTasks) : [];
  }

  // Load tasks on component mount
  import { onMount } from "svelte";
  onMount(loadData);

  // TODO: Add feature to edit existing tasks
// TODO: Add confirmation before removing a task


</script>







<main>
    <div class="container">
        <div class="todo-app">
          <h2>
            To-Do List
            <img
              src="https://cdn.jim-nielsen.com/watchos/512/minimalist-to-do-list-task-2020-03-09.png?rf=1024"
              alt="check mark"
            />
          </h2>
      
          <div class="text-field">
            <input
              type="text"
              bind:value={input}
              placeholder="Add your task"
              on:keyup={(e) => e.key === 'Enter' && addTask()}
            />
            <button on:click={addTask}>Add</button>
          </div>
      
          <ul>
            {#each tasks as task, index}
              <li
                class:checked={task.completed}
                on:click={() => toggleTask(index)}
              >
                {task.text}
                <span on:click={(e) => { e.stopPropagation(); removeTask(index); }}>&times;</span>
              </li>
            {/each}
          </ul>
        </div>
      </div>
      

</main>


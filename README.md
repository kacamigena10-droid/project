// Merr te dhenat nga formulari dhe krijon nje detyre te re.
const form = document.getElementById("taskForm");

form.addEventListener("submit", function(event) {
  event.preventDefault();

  const title = document.getElementById("taskTitle").value.trim();
  const description = document.getElementById("taskDescription").value.trim();
  const date = document.getElementById("taskDate").value;
  const priority = document.getElementById("taskPriority").value;

  if (!title) return;

  const tasks = JSON.parse(localStorage.getItem("taskflow_tasks") || "[]");
  const newTask = {
    id: Date.now(),
    title: title,
    description: description,
    date: date,
    priority: priority,
    completed: false
  };

  tasks.push(newTask);
  localStorage.setItem("taskflow_tasks", JSON.stringify(tasks));

  document.getElementById("formMessage").textContent = "Detyra u ruajt me sukses!";
  form.reset();

  setTimeout(() => {
    window.location.href = "index.html";
  }, 700);
});


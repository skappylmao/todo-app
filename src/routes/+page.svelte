<script lang="ts">
  import { Label, Input, Button } from "flowbite-svelte";
  import TodoTable from "../components/TodoTable.svelte";


  let todo = "";
  let todoList: { id: number; todo: string; completed: boolean }[] = [
    {
      id: 0,
      todo: "Welcome to my todo list!",
      completed: false,
    },
  ];
  function addTodo() {
    todoList.push({
      id: todoList.length,
      todo: todo,
      completed: false,
    });
    todoList = todoList;
  }

  function removeTodo(id: number) {
    let temp = todoList.filter((item) => item.id !== id);
    todoList = todoList.filter((item) => item.id !== id);
    todoList = temp;
  }

  function saveTodo() {
    
  }
</script>

<div class="mb-6 m-16">
  <Label for="large-input" class="block mb-2">Add to-do entry</Label>
  <Input
    id="large-input"
    size="lg"
    placeholder="Thing to do"
    bind:value={todo}
  />
  <Button class="mt-4" on:click={addTodo}>Add</Button>
</div>

<div class="m-16 p-4 bg-slate-200 rounded-lg">
  <TodoTable data={todoList} {removeTodo} />
</div>

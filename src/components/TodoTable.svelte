<script lang="ts">
  import {
    Table,
    TableBody,
    TableBodyCell,
    TableBodyRow,
    TableHead,
    TableHeadCell,
    Checkbox,
  } from "flowbite-svelte";
  export let data: { id: number; todo: string; completed: boolean }[];
  export let removeTodo: (id: number) => void;
</script>

<Table class="bg-slate-200 rounded-lg">
  <TableHead>
    <TableHeadCell class="!p-4">
      <Checkbox />
    </TableHeadCell>
    <TableHeadCell>Number</TableHeadCell>
    <TableHeadCell>To do item</TableHeadCell>
    <TableHeadCell>Completed</TableHeadCell>
    <TableHeadCell>
      <span class="sr-only"> Delete </span>
    </TableHeadCell>
  </TableHead>

  <TableBody>
    {#each data as item, index (item.id)}
      <TableBodyRow>
        <TableBodyCell class="!p-4">
          <Checkbox bind:checked={item.completed} />
        </TableBodyCell>
        <TableBodyCell>{index + 1}</TableBodyCell>
        <TableBodyCell>{item.todo}</TableBodyCell>
        <TableBodyCell>{item.completed}</TableBodyCell>
        <TableBodyCell>
          <!-- svelte-ignore a11y-invalid-attribute -->
          <a
            href="#"
            class="font-medium text-primary-600 hover:underline dark:text-primary-500"
            on:click={() => removeTodo(item.id)}
          >
            Remove
          </a>
        </TableBodyCell>
      </TableBodyRow>
    {/each}
  </TableBody>
</Table>

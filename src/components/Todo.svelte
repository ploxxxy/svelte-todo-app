<script>
    import { deleteTodo, toggleTodoCompleted } from "../store/todoStore";
    export let todo
</script>

<div class="alert bg-base-100 my-1 flex flex-row">
    <input type="checkbox" name="completed" checked={todo.completed} on:change={() => toggleTodoCompleted(todo.id)}
    class="mr-2 checkbox checkbox-primary h-5 w-5">
    <span class={`flex-1  ${todo.completed ? 'line-through' : ''}`}>{todo.text}</span>
    <button type="button" class="btn btn-sm btn-accent" on:click={() => deleteTodo(todo.id)}>Delete</button>
</div>
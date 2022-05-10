<script>
    import TodoForm from '../components/TodoForm.svelte'
    import Todo from '../components/Todo.svelte'
    import { todos } from '../store/todoStore'
</script>

<main class="mockup-window bg-base-200 p-4 m-4 md:m-0">
    <h1 class="text-2xl font-bold text-center md:text-3xl">
        My ToDos
    </h1>
    <TodoForm />
    {#each $todos as todo}
        <Todo todo={todo} index={todo.id} />
    {/each}
</main>
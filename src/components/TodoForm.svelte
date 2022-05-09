<script>
    import { addTodo } from '../store/todoStore'
    import { user } from '../store/authStore'
    let todo = ''

    const handleSubmit = () => {
        addTodo(todo, $user.id)
        todo = ''
    }
</script>

<form class="my-6" on:submit|preventDefault={handleSubmit}>
    <div class="flex flex-col text-sm mb-2">
        <label class="font-bold mb-2" for="todo">Todo</label>
        <input class="appearance-none shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg" 
        type="text" bind:value={todo} name="todo" placeholder="What to do?">
    </div>
    <button class="w-full shadow-sm rounded bg-blue-600 hover:bg-blue-700 text-white py-2 px-4" type="submit">Submit</button>
</form>
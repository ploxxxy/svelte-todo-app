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
    <div class="form-control w-full">
        <label class="label" for="todo">
          <span class="label-text">Todo</span>
        </label>
        <input type="text" bind:value={todo} placeholder="What to do?" class="input input-bordered w-full" />
        <button type="submit" class="btn btn-primary w-full my-2">Submit</button>
      </div>
</form>
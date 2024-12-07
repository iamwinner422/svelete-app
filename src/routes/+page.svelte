<script lang="ts">
    interface Todo {
        text: string;
        done: boolean
    }
    let todos: Array<Todo> = [
        {text: 'By some milk', done: false},
        {text: 'By some bread', done: false},
        {text: 'By Google', done: true},
        {text: 'Go to the moon🚀', done: true}
    ];
    let newtodo: string = '';

    function addTodo(): void {
        todos = [...todos, {text: newtodo, done: false}]
        newtodo = '';
    }

    function removeTodo(index: number): void {
        todos = todos.filter((_, i) => i !== index);
    }
</script>

{#each todos as todo, i}
    <p>
        <input type="checkbox" name="todo-{i}" id="todo-{i}" bind:checked={todo.done}/>
        {i+1}. {todo.text}
        <button type="button" on:click|preventDefault={() => removeTodo(i)}>x</button>
    </p>
{/each}
<form action="#" on:submit|preventDefault={addTodo}>
    <input type="text" name="todo" id="todo" bind:value={newtodo}/>
    <button type="submit">+</button>
</form>
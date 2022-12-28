<script>
	let userInput = '';
	let todoList = [];

	function handleSubmit() {
		let newTodo = {
			title: userInput,
			id: todoList.length + 1,
			compleated: false
		};

		todoList = [...todoList, newTodo];
		userInput = '';
	}

	function handleDeleteTodo(id) {
		todoList = todoList.filter((todo) => todo.id != id);
	}
</script>

<div class="outmost__container">
	this is the TodoList
	<div class="todo__list__container">
		<form on:submit|preventDefault={handleSubmit}>
			<input type="text" bind:value={userInput} />
			<button type="submit">Add Todo</button>
		</form>
		<div class="list__container">
			<ul class="order__list">
				{#each todoList as todo}
					<div class="todo__card">
						<li>{todo.title}</li>
						<button on:click={() => handleDeleteTodo(todo.id)}>delete</button>
					</div>
				{/each}
			</ul>
		</div>
	</div>
</div>

<style>
	.outmost__container {
		height: 400px;
		width: 400px;
		background-color: whitesmoke;
	}
	.todo__list__container {
		height: 100%;
		width: 100%;
		background-color: brown;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.list__container {
		height: 300px;
		width: 225px;
		background-color: white;
	}
	.todo__card {
		display: flex;
		height: 100%;
		width: 120px;
		background-color: lightgray;
		justify-content: space-between;
	}
	.order__list > * {
		margin-top: 10px;
	}
</style>

<script>
    let newItem = '';
	
    let todoList = [{text: 'Write my first post', status: true},
                    {text: 'Upload the post to the blog', status: false},
                    {text: 'Publish the post at Facebook', status: false}];
	
	function addToList() {
		todoList = [...todoList, {text: newItem, status: false}];
		newItem = '';
	}
	
	function removeFromList(index) {
		todoList.splice(index, 1)
		todoList = todoList;
    }
</script>

<div class='main'>
    <div class='input'>
        <input bind:value={newItem} type="text" placeholder="What needs to be done?">
        <button on:click={addToList}>Add</button>
    </div>
    
    <br/>
    
    <div class='counter'>
        <span class='main'>To-Dos: {todoList.length}</span>
        <div class='actionable'>
            <strong class='active'>Active: {todoList.filter(i => i.status ===false).length}</strong>
            <hr role="separator" aria-orientation="vertical"/>
            <strong class='completed'>Completed: {todoList.filter(i => i.status).length}</strong>
        </div>
    </div>
    
    <br/>

    <div class='todo-list'>
        {#each todoList as item, index}
            <div class='paper-task'>
                <div class='task-actions'>
                    <span class="delete" on:click={() => removeFromList(index)}>❌</span>
                </div>
                <div class='task-name'>
                    <input bind:checked={item.status} type="checkbox">
                    <span class:checked={item.status}>{item.text}</span>
                </div>
            </div>
            <br/>
        {/each} 
    </div>
</div>


<style> 
    .main {
        padding: 20px;
        display: flex;
        flex-direction: column;
        font-family: 'Roboto', sans-serif;
    }
    .input {
        width: 100%;
    }
    .input input {
        width: 90%;
        height: 60px;
    }
	.checked {
        text-decoration: line-through;
    }
    .counter {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }
    .counter .main {
        font-size: 2.125rem;
        color: #7b1fa2;
        padding: 0px;
    }
    .actionable {
        margin: 4px;
        display:flex;
        justify-content: space-between;
    }
    .actionable .active {
        margin-right: 10px;
        color: #c2185b;
    }
    .actionable .completed {
        color: #f57c00;
    }
    .todo-list {
        width: 100%;
    }
    div .paper-task {
        width: 100%;
        height: 120px;
        padding:0px;
        background-color: #90CAF9;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
        border-radius: 5px;
        transition: box-shadow .8s;
    }
    .paper-task .task-name {
        width: 100%;
        height: 100%;
        /* background-color: green; */
        color: white;
        margin-left: 20px;
        line-height: 2rem;
        font-size: 1.5rem;
        font-weight: 400;
    }
    .paper-task .task-actions {
        width: 100%;
        display: flex;
        justify-content:flex-end;
        margin-right: 20px;
    }
    .paper-task .task-actions .delete :hover {
        cursor: pointer
    }

</style> 
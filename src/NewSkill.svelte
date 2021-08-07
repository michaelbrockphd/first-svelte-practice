<script>
    export var clbkAddSkill;

    let title;

    const onClickAdd = () => {
        if(clbkAddSkill) {
            if(clbkAddSkill(title)) {
                title = ""
            }
        }
    };
</script>

<div class="new_container">
    <input bind:value={title} type="text" />

    <button on:click={onClickAdd}>Add</button>
</div>

<style lang="scss">
    .new_container {
        display: flex;
        flex-direction: row;

        input {
            flex-grow: 4;
        }

        button {
            flex-grow: 1;
        }
    }

</style>

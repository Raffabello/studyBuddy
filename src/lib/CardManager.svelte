<script lang="ts">
    let enteredWord = "";
    let cards:string[] = [];
function addWordToList(){
    if (enteredWord.trim()) {
      cards = [...cards, enteredWord]; //using the spread operator add the last word added ent to the array
      enteredWord = '';
    }
}  
</script>

<div id="display">
<div id="card-manager">
    <div id="card-manager-header">
        <input type="text" placeholder="Think a word ..." bind:value={enteredWord}/>
        <input type="button" value="Enter" on:click={addWordToList}/>
    </div>
    <div id="card-manager-body">
        {#each cards as word}
        <div class="word-card">
            <div class="word-card-left">{word}</div>
            <div class="word-card-right" contenteditable="true">Meaning</div>
        </div>
        {/each}
    </div>
</div>
</div>


<style>
    #card-manager-body{
        display:flex;
        flex-direction: column;
        justify-content: center;
    }

    .word-card{
        display:flex;
        border:1px solid black;
    }

    .word-card div{
        width:50%;
    }

</style>
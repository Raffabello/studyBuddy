<script lang="ts">
    let enteredWord = "";
    let cards:string[] = [];
function addWordToList(){
    if (enteredWord.trim()) {
      cards = [...cards, enteredWord]; //using the spread operator add the last word added ent to the array
      enteredWord = '';
    }
}  

function readWord(event){
    let word = event.srcElement.innerText;
    if(word){
        const wordToRead = new SpeechSynthesisUtterance(word);
        speechSynthesis.speak(wordToRead);
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
            <button class="word-card-left" on:click={readWord}>{word}</button>
            <div class="word-card-right" contenteditable="true">Meaning</div>
        </div>
        {/each}
    </div>
    <div id="settings">
        <p>App Settings:</p>
        <div id="select-language">
            <div>
                <span>Left Language</span>
                <select id="left-language-select">
                    
                </select>
            </div>
            <div>
                <span>Right Language</span>
                <select id="right-language-select">
                    
                </select>
            </div>
        </div>
    </div>
</div>
</div>


<style>
    #card-manager-body{
        display:flex;
        flex-direction: column;
        justify-content: center;
        padding:12px;
    }

    .word-card{
        display:flex;
        padding:3px;
        
        border:1px solid black;
        border-radius:5px;
        margin-bottom:5px;
    }

    .word-card div{
        width:50%;
    }

    #select-language{
        width:50%;
        display:grid;
        grid-template-columns: 1fr 1fr;
    }

</style>
<script>
    export let navigateTo;
    //example data
    let user = "Anita Varøy";
    let pollQuestion = "Pineapple on pizza: Is it ok?"
    let pollId = 42;

    let pollOptions = [
        {caption: "Det er digg!", numOfVotes: 1},
        {caption: "Hell no!",  numOfVotes: 34},
        {caption: "Could not care less", numOfVotes: 12}
    ];

    //Funksjon som håndterer inkrement og dekrement av stemmer
    function vote(option, upOrDown){
        if(upOrDown === "upvote"){
            option.numOfVotes++;
        }else if(upOrDown === "downvote"){
            option.numOfVotes--;
        }
    }
</script>
<style>
    .poll-container{
        margin: 20px;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 10px;
    }
    .poll-question{
        font-size: 1.5em;
        margin-bottom: 15px;
    }
    .poll-options{
        list-style: none;
        padding: 0;
    }

    .buttons{
        display: flex;
        gap: 5px;
    }
    .upvote, .downvote{
        border: none;
        padding: 5px 10px;
        border-radius: 5px;
        cursor: pointer;
    }
    .vote{
        background-color: green;
        color: white;
    }
    .votes{
        margin-left: 10px;

    }


</style>

<div class="poll-container">
        <h1>Hello {user}</h1>

    <div>
        <span>
            Poll #{pollId}
        </span>
        <h2 class="poll-question"> {pollQuestion}</h2>
    </div>

    <ul class="poll-options">
        {#each pollOptions as option}
        <li class="option-items">
            <span>{option.caption}</span>
            <div class="buttons" >
                <button class="vote" on:click={() => vote(option, "upvote")} ></button>
                <span class="votes">{option.numOfVotes}</span>
            </div>
        </li>
            {/each}
    </ul>
    <h3>Poll component</h3>
    <button on:click={() => navigateTo("Create")}>Go to Create poll</button>
</div>
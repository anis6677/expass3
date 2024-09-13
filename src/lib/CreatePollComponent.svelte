<script>
    export let navigateTo;
    let question;
    let publishedAt;
    let validUntil
    let creator;
    let liste =[
        {caption: ""},
        {caption: ""},
        {caption: ""},
    ]

    //function to create poll
    function createPoll(inputQuestion, inputListe){
        publishedAt = Date.now();
        validUntil = Date.UTC(2025 );
        question = inputQuestion;
        creator = {username: "Anita", email: "anita@mail.com"};
        liste = inputListe;
    }

</script>
<style>
    .poll-container{
        margin: 20px;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 100px;
    }
    input{
        height: 50px;
        width: 100px;
    }
    .button{
        display: flex;
        gap: 5px;
    }
    .add{
        background-color: green;
        color: white;
    }



</style>

<div class="poll-container">
    <h1>Lag meningsmåling</h1>
    <input bind:value={question} placeholder="Legg til et spørsmål"/>
    <ul>
    <input bind:value={liste[0].caption} placeholder="legg til"/>
    <input bind:value={liste[1].caption} placeholder="legg til"/>
    <input bind:value={liste[2].caption} placeholder="legg til"/>
    <div class="button">
        <button class="add" on:click={() => createPoll(question, liste)}></button>
    </div>
    </ul>
    <h2>Go back to polls</h2>
    <button on:click={() => navigateTo("Poll")}>Back to polls</button>
</div>
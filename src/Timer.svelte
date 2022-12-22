<script>
    import ProgressBar from "./ProgressBar.svelte"; 

    const totalSecons =2;
    let secondLeft = totalSecons;
    let isRunning =false;
    
    $:progress =((totalSecons - secondLeft)/totalSecons)*100;

    let startTimer = () =>{
        if(!isRunning){
            debugger;
            isRunning=true;
            let timer = setInterval(()=>{
                secondLeft-=1;
                if(secondLeft==0){
                    clearInterval(timer);
                    isRunning=false;
                    secondLeft=totalSecons;
                }                    
            },1000);
        }
        
    }
    
</script>
<style>
    h2{
        margin: 0;
    }
    .start{
        background-color: rgb(154,73,73);
        width: 100%;
        margin: 10pox 0;
    }
    .start[disabled]{
        background-color: rgb(194, 194, 194);
        cursor: not-allowed;
    }
</style>
<div bp="grid">
    <h2 bp="offset-5@md 4@md 12@sm">
        Seconds Lefts: {secondLeft}
    </h2>
</div>

<ProgressBar {progress}/>
<button disabled={isRunning} class="start" bp="offset-5@md 4@md 12@sm" on:click={startTimer}> 
    Start
</button>


<script>

    let board = [" ", " ", " "," ", " ", " "," ", " ", " "]
    let isPressedBoard = [false, false, false, false, false, false, false, false, false]
    let currentPlayer = "X"
    
    function handleClick(index){

        if (board[index] === " ") {

            isPressedBoard[index] = true
            board[index] = currentPlayer

            const winner = checkWin()
            if ( winner != -1){
                console.log(winner+" has won!")
            }
            currentPlayer = (currentPlayer== "X"? "O": "X")


            setTimeout(() => {
                isPressedBoard[index] = false
            }, 500);
        }



    }
    function checkWin(){
        
        if ((board[0] == board[1])&&(board[1] == board[2]) && board[0] != " "){
            return board[0]
        }
        if ((board[3] == board[4])&&(board[4] == board[5]) && board[3] != " "){
            return board[3]
        }
        if ((board[6] == board[7])&&(board[7] == board[8]) && board[6] != " "){
            return board[6]
        }

        if ((board[0] == board[3])&&(board[3] == board[6]) && board[0] != " "){
            return board[0]
        }
        if ((board[1] == board[4])&&(board[4] == board[7]) && board[1] != " "){
            return board[1]
        }
        if ((board[2] == board[5])&&(board[5] == board[8]) && board[2] != " "){
            return board[2]
        }

    
        if ((board[0] == board[4])&&(board[4] == board[8]) && board[0] != " "){
            return board[0]
        }
    
        if ((board[2] == board[4])&&(board[4] == board[6]) && board[2] != " "){
            return board[2]
        }
        return -1
    }

    
</script>

<div id="board">
    {#each board as slot, index }

    <div class="slot {isPressedBoard[index]? "pressed": ""}" on:click={()=>{handleClick(index)}}>
        {slot}
    </div>
        
    {/each}
</div>

<style lang="scss">

    #board{
        display: inline-grid;
        grid-template-columns: 100px 100px 100px;
        grid-template-rows: 100px 100px 100px;

        border: thick rgb(255, 255, 255) solid;
        border-radius: 70px;
        margin: 10px;

        
    }
    .slot{
        display: flex;
        width: auto;

        color: white;
        background-color: rgb(236, 158, 158);
        border: thick rgb(255, 255, 255) ridge;
        margin: 5px;

        font-size: 4rem;
        font-family: Arial, Helvetica, sans-serif;
        align-items: center;
        justify-content: center;


        transition: transform 0.2s;
        transition: background-color 0.1s;
        &.pressed{
            transform: scale(0.9);
            background-color: rgb(230, 81, 81);
        }





    }

</style>
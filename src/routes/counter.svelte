<script>

    let count = 0
    let buttonText = "Click"+count
    let isPressed = false

    function handleClick(){
        count+= 1
        isPressed = true
        buttonText = "Clicked!"

        setTimeout(() => {


            buttonText = "Click"+count
            isPressed = false
            
        }, 500);


    }
</script>

<button on:click={handleClick} class={isPressed? "pressed": ""}>

    {buttonText}
</button>

<style lang="scss">

    button {
        transition: transform 0.1s;

        &.pressed{
            transform: scale(0.9); /* Slightly shrink button when pressed */
            color: rgb(255, 0, 128);

        }
        
    }
    


</style>
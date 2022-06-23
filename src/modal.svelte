<script>
 export let showModal=false;
 export let isPromo=true; //lets data from another page show
 export let message ="default value of prop";
 let show =false;
 const showIt=()=>{
     show= !show;
 } 
</script>

{#if showModal}
<div class="backdrop" on:click|self> <!-- event modifiers self-->
    <div class="wrap">
        <button class="close" on:click>&#10060;</button>

        <slot name="title"></slot>
        <slot></slot>

        <p class:promo={isPromo}>Hello form the modal !</p>
        <p>{message}</p>
        <!-- event modifiers Once-->
        <div>
            <button on:click|once={showIt}>click </button>
            {#if show}
                <div>
                    <svg style="width:20px ;height:20px;" xmlns="http://www.w3.org/2000/svg"  fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 15.546c-.523 0-1.046.151-1.5.454a2.704 2.704 0 01-3 0 2.704 2.704 0 00-3 0 2.704 2.704 0 01-3 0 2.704 2.704 0 00-3 0 2.704 2.704 0 01-3 0 2.701 2.701 0 00-1.5-.454M9 6v2m3-2v2m3-2v2M9 3h.01M12 3h.01M15 3h.01M21 21v-7a2 2 0 00-2-2H5a2 2 0 00-2 2v7h18zm-3-9v-2a2 2 0 00-2-2H8a2 2 0 00-2 2v2h12z" />
                    </svg>
                    <svg style="width:20px ;height:20px;" xmlns="http://www.w3.org/2000/svg"  fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z" />
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z" />
                    </svg>
                    <svg style="width:20px ;height:20px;" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v13m0-13V6a2 2 0 112 2h-2zm0 0V5.5A2.5 2.5 0 109.5 8H12zm-7 4h14M5 12a2 2 0 110-4h14a2 2 0 110 4M5 12v7a2 2 0 002 2h10a2 2 0 002-2v-7" />
                    </svg>
                    <svg style="width:20px ;height:20px;" xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M18 8a6 6 0 01-7.743 5.743L10 14l-1 1-1 1H6v2H2v-4l4.257-4.257A6 6 0 1118 8zm-6-4a1 1 0 100 2 2 2 0 012 2 1 1 0 102 0 4 4 0 00-4-4z" clip-rule="evenodd" />
                    </svg>
                    <svg style="width:20px ;height:20px;" xmlns="http://www.w3.org/2000/svg"  fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
                    </svg>
                </div>
            {/if}
        </div>
    </div>
</div>
{/if}

<style>
    .backdrop{
        background-color: rgb(0,0, 0,0.8);
        width:100%;
        height:100%;
        position: fixed;
    }
    .wrap{
        background-color:snow;
        max-width: 400px;
        padding:10px;
        margin: 30px auto;
        text-align: center;
        border-radius: 20px;
    }
    .wrap .promo{
        color:red;
    }
    .close{
        text-align: right;
        width: fit-content;
        height: fit-content;
        display: flex;
      
    }


</style>
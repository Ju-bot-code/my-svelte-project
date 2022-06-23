    <script>
        import {createEventDispatcher} from 'svelte';

        let myEvent=createEventDispatcher();
    
        let user;
        let beltColor;
        let age;
        let hobby;
        let skills=[];
        const submitForm=()=>{

           const newuser={ 
           name:user,
            beltColor,  
            age,//or -->  age:age,
            skills, //or -->  skills:skills,
            id:Math.random().toString(3).slice(30),
            hobby
        }

            myEvent('addUser',newuser);

            // console.log(user,beltColor,age,skills);
        }
    </script>
    <!-- event -->

    <form on:submit|preventDefault={submitForm}>
        <input type="text" placeholder="name" bind:value={user}><!-- input -->
        <input type="text" placeholder="hobby" bind:value={hobby}><!-- input -->
        <br>
        <!-- <input type="text" placeholder="beltColor" bind:value={beltColor}> -->
        <br>
        <label>Belt Color:</label>
        <select bind:value={beltColor}><!-- drop down -->
            <option value="Black">Black</option>
            <option value="brow">brow</option>
            <option value="Green">Green</option>
            <option value="Yellow">Yellow</option>
            <option value="white">white</option>
        </select>
        <br>
        <input type="number" placeholder="age" bind:value={age}><!-- number -->

        <div>
            <label>skills:</label>

            <input type="checkbox" bind:group={skills} value="punching">Punching<br>
            <input type="checkbox" bind:group={skills} value="Running">Running<br>
            <input type="checkbox" bind:group={skills} value="Kicking">Kicking<br>
        </div>

        
        <button>submit</button>
    </form>

    <style>

    </style>
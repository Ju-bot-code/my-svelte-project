<script>
	import Modal from './modal.svelte';
	import ModalForm from './forms.svelte';

	 let name='people';
	 let color='red';


	 // on click function 
	 const clicking =()=>{
			color='pink';
	 }

	 // on:input function 
	 const typing =(e)=>{
		color=e.target.value ;
	 }

	 // two way binding 
	 let pet ='two';

	 const set=()=>{
		 pet='three';
	 }
	 const petCount=(e)=>{
	pet=e.target.value;
	 }
	
	 //bind key word
	 let season='summer'

	 // css
	 let size ='25px';
	 let background="blue";
	 let textColor='gray';


	 //Reactive value
	let firstName ='Monica'
	let lastName ='Galler'
	let designations ='developer'

	$:fullName=`${firstName} ${lastName}`; 

	// Reactive statement 
	// almost performs like a event listener 

	//single
	$:console.log(firstName); // will log everytime theres a change 

	// muiltiple
	//everytime any one of the varibale chnages it logs the entier group ..
	$:{	
		console.log(lastName);
		console.log(color);
		console.log(designations); 
	}


	//FOR EACH
	let people=[
		{name:'jade',hobby:'painting',id:1,beltcolor:'black',age:20,skills:[]},
		{name:'veronica',hobby:'singing',id:2 ,beltcolor:'blue',age:25,skills:[]},
		{name:'luca',hobby:'potery',id:3,beltcolor:'brown',age:29,skills:[]},
		{name:'jamey',hobby:'travelling',id:4,beltcolor:'purple',age:30,skills:[]},
		{name:'timathy',hobby:'coin collecting',id:5,beltcolor:'black',age:32,skills:[]}
	]
	let message ='<strong>Black Belt </strong>';

	//delete user
	const deleteuser=(id)=>{
		people=people.filter((people)=> people.id != id);
	}

	//if condition
	let num=25;
	const more=()=>{
		num +=1;
	}
	const less=()=>{
		num -=1;
	}

	//modal
	let showModal = false;
	let modalToggle=()=>{
		showModal= !showModal;
	};

	const addUser=(e)=>{
		// console.log(e.detail);
		let newuser=e.detail;
		people=[newuser,...people];  
		showModal=false;
	}

	


</script>

	<Modal 
	message="this is a value from a prop " 
	isPromo={false}
	{showModal} on:click={modalToggle} >

	<!-- named slot -->
	<h3 slot="title">Add User</h3>


	<!-- un-named slot -->
	<div> 
		<ModalForm on:addUser={addUser}/>
	
	</div>

	</Modal>

	
<!-- isPromo is inside brackets since its not a string -->

<main>
	<!-- displays a value from the variable  -->
	<h1>Hello  <span class="space">{name}!</span> </h1>

	<hr>
	<hr>
	<!-- on click chnages value of the varibale color -->
	<p style="color:{color}">{color}</p>
	<button on:click={clicking}>click me </button> 


	 <!-- chnages the value of variable color or type  -->
	<input style="color:{color}"  type="text" name="" id="" on:input={typing}>


	<!-- binds the data of one input to another  -->
	<input  bind:value={color} style="display:block;text-align:center; color:{color}"  type=text name="" >

	<hr>
	<hr>
	<!-- two way binding  -->
	<h3>two way binding </h3>

	<h4> I have {pet}  pets  </h4>
	<input type="text" name="" id="" on:input={petCount} value={pet}>
	<button on:click={set}>set </button>

	<hr>
	<hr>

	<!-- two way binding  with bind key word -->
	<h3>two way binding  with bind key word </h3>
	<p>its {season} season</p>
	<input type="text" bind:value={season}>

	<hr>
	<hr>
	<!-- Some Css fun -->
	<h3>svelte with css</h3>
	<!-- <br> -->
	<p style="background-color: {background}; font-size: {size};color:{textColor}">lets play with sum CSS</p>
	<input type="text" bind:value={size}>
	<input type="text" bind:value={background}>
	<input type="text" bind:value={textColor}>

	<hr>
	<hr>
	<!--Reactive value-->
	<h3>Reactive value</h3>
	<h2>{fullName} <br> Designation: {designations}</h2>
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={designations}>


	<hr>
	<hr>

	<!-- if condition -->
	<h3>if condition</h3>
	
	{#if num >25}
	<p>num is greater than 25</p>
	{:else if num >10}
	<p>numb is greater than 10</p>
	{:else}
	<p>less than 10</p>
	{/if}
	<h4>{num}</h4>
	<button on:click={less}>-</button>
	<button on:click={more}>+</button>

	<hr>
	<hr>
	<h3>For Eaching in svelte</h3>

	<h2>Users and thier hobby's</h2>
	{#each people as user (user.id)} 
	<!-- always a good practice to use any kind of id so the 
		DOM can keep track of the data thats being foreached  -->
	<div>
	<p>
		<span>-{user.id}</span>
		 {user.name} enjoys {user.hobby} 

		 {#if user.beltcolor === 'black'}
		<span> , {@html message} .</span> 
		{:else}
		.
		{/if}

	</p>
	
	</div>
	{:else} <!-- if no data exists to foreach  -->
	<div> sorry no users exist</div>
	{/each}


	<hr>
	<hr>
	<!-- deleting users -->
	<div class="text-align:left;background-color:pink;">
		<h3>Add/Delete user</h3>

		<nav style="text-align:left;padding:4px;margin:0px;">
			<button on:click={modalToggle}>open</button>
		</nav>

		<h2>Users and thier hobby's</h2>

		{#each people as user (user.id)} 
			<!-- always a good practice to use any kind of id so the 
				DOM can keep track of the data thats being foreached  -->
			<div>
				<p>
					<span>
						<svg style="width:20px ;height:20px;" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.121 17.804A13.937 13.937 0 0112 16c2.5 0 4.847.655 6.879 1.804M15 10a3 3 0 11-6 0 3 3 0 016 0zm6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
						</svg>
					{user.id}
					</span> 
						{user.name} enjoys {user.hobby},<br>
						Is {user.age} years old,<br>


						skills: <br>
							
							{#each user.skills as skill}
							<p>{skill}</p>
							{:else}
							<p>NO SKILLS</p>

							{/each}

					<button on:click={()=>deleteuser(user.id)}>delete</button>
				</p>
			</div>
		{:else} <!-- if no data exists to foreach  -->
			<div> sorry no users exist</div>
		{/each}
	</div>


	




	<!-- <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p> -->
</main>

<style>

	.space{
		margin: 0px 25px;
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	nav{
		width:100%;
		height:min-content;
		background-color: coral;
	}
	button {
		margin:2px;
		border-radius: 20px;
	}
	hr{
		border-top: 1px dashed rgb(207, 152, 152);
	}
</style>
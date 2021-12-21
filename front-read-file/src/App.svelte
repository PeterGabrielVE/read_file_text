
<script>
	export let name;
	let postVar;
	let fileVar;
  
	function submitForm(){
	  event.preventDefault();
  
	  const dataArray = new FormData();
	  dataArray.append("nameFile", postVar);
	  dataArray.append("uploadFile", fileVar);
	  //fetch("https://www.example.com/uploadFile.php", {
	   fetch("api_url_aca", {
		method: "POST",
		headers: [["Content-Type", "multipart/form-data"]],
		body: dataArray
	  })
		.then(response => {
		  // Successfully uploaded
		})
		.catch(error => {
		  // Upload failed
		});
	}
  </script>

<main>
	<h1>Read {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p><br/>
	<form on:submit={submitForm}>
		<div class="flex justify-center">
			<div class="mb-3 w-96">
				<label for="formFile" class="form-label inline-block mb-2 text-gray-700">Ingresa el nombre</label>
				<input class="form-control
				block
				w-full
				px-3
				py-1.5
				text-base
				font-normal
				text-gray-700
				bg-white bg-clip-padding
				border border-solid border-gray-300
				rounded
				transition
				ease-in-out
				m-0
				focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none" type="text" id="formFile"   bind:value={postVar}
				placeholder={"Nombre archivo"} required/>

				<label for="formFile" class="form-label inline-block mb-2 text-gray-700">Ingresa el archivo txt</label>
				<input class="form-control
				block
				w-full
				px-3
				py-1.5
				text-base
				font-normal
				text-gray-700
				bg-white bg-clip-padding
				border border-solid border-gray-300
				rounded
				transition
				ease-in-out
				m-0
				focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none" type="file" id="formFile"    bind:files={fileVar} required/>
			</div>
		</div>
		 <input type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" />
		 
	</form>

	
</main>

<style global>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
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
</style>
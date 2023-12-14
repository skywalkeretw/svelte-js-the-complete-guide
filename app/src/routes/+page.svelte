<script>
    import ContactCard from "./ContactCard.svelte";
  
    let name = "Max";
    let jobTitle = ""
    let description = ""
    let userImg =""
    let age = 30;
    let fun = ""
    let funStyle = false
    // let uppercaseName; not required!
  
    $: uppercaseName = name.toUpperCase();
  
    $: console.log(name);
  
    $: if (name === "Maximilian") {
      console.log("It runs!");
      age = 31;
    }

    $: fun.includes("!") ? funStyle = true : funStyle = false
  
    function incrementAge() {
      age += 1;
    }
  
    function changeName() {
      name = "Maximilian";
    }
  
    function nameInput(event) {
      const enteredValue = event.target.value;
      name = enteredValue;
    }
  </script>
  
  <style>
    h1 {
      color: purple;
    }

    .fun {
        color: red;
    }
  </style>
  
  <h1>Hello {uppercaseName}, my age is {age}!</h1>
  <button on:click={incrementAge}>Change Age</button>
  <!-- <button on:click="{changeName}">Change Name</button> -->
  <!-- <input type="text" value={name} on:input={nameInput} /> -->
  <input type="text" bind:value={name} />
  <input type="text" bind:value={jobTitle} />
  <input type="text" bind:value={userImg} />
  <textarea rows="3" bind:value={description}></textarea>
  <input type="text" bind:value={fun} class:fun={funStyle}/>
  <ContactCard userName="{name}" jobTitle="{jobTitle}" {userImg} {description} />
  
  <div if:{funStyle}>

  </div>
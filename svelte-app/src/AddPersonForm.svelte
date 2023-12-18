<script>
  let name;
  let beltColor;
  let age;

  // let fighting = false;
  // let sneaking = false;
  // let running = false;

  let skills = [];

  const handleSubmit = () => {
    console.log(name, beltColor, age, skills);
  };
</script>

  <!-- The preventDefault event modifier is used to stop the automatic refreshing for an html form  -->
  <!-- that happens every time an HTML form is submitted. -->
<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name}>
  <!-- <input type="text" placeholder="belt colour" bind:value={beltColor}> -->
  <input type="number" placeholder="age" bind:value={age}>

  <label>Skills:</label>

  <!-- THE STANDARD WAY TO BIND CHECKBOX3S --> 
  <!-- <input type="checkbox" checked={fighting}>Fighting<br> -->
  <!-- <input type="checkbox" checked={sneaking}>Sneaking<br> -->
  <!-- <input type="checkbox" checked={running}>Running<br> -->

  <input type="checkbox" bind:group={skills} value="fighting">Fighting<br>
  <input type="checkbox" bind:group={skills} value="sneaking">Sneaking<br>
  <input type="checkbox" bind:group={skills} value="running">Running<br>

  <label for=""> Belt Color:</label>
  <select bind:value={beltColor}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>

  <button>Add Person</button>

</form>

<style>

</style>

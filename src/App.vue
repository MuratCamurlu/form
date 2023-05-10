<template>
  <div class="main">
    <div class="wrapper">
      <form class="myForm">
        <div class="inputDiv">
          <label for="nameInput">Name</label>
          <input type="text" id="nameInput" placeholder="Please enter a name" />
        </div>
        <div class="inputDiv">
          <label for="surnameInput">Surname</label>
          <input
            type="text"
            id="surnameInput"
            placeholder="Please enter a surname"
          />
        </div>
        <div class="inputDiv">
          <label for="email">Email</label>
          <input type="email" id="email" placeholder="Please enter a email" />
        </div>
        <div class="inputDiv">
          <label for="country">Country</label>
          <select name="country" id="country" class="select">
            <option>France</option>
            <option>Germany</option>
            <option>England</option>
          </select>
        </div>

        <div class="inputDiv">
          <label for="addressInput">Address</label>
          <textarea name="address" id="addressInput" rows="5" />
        </div>
        <button type="submit" class="submitBtn">Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
};
</script>

<style>
input {
  padding: 5px;
}
.main {
  width: 100%;
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}
.wrapper {
  width: 80%;
  box-shadow: 1px 3px 3px 1px;
  padding: 10px;
  border-radius: 10px;
}
.myForm {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.inputDiv {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.submitBtn {
  border: none;
  padding: 8px;
  border-radius: 10px;
  color: white;
  background-color: blue;
  cursor: pointer;
}
.submitBtn:hover {
  color: white;
  background-color: navy;
}
.select {
  padding: 5px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}
</style>

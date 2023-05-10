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
        <div class="inputDiv">
          <h4>Hobbies</h4>
          <div class="checkboxDiv">
            <div>
              <label for="checkbox1">Football</label>
              <input type="checkbox" id="checkbox1" name="checkbox1" />
            </div>
            <div>
              <label for="checkbox2">Basketball</label>
              <input type="checkbox" id="checkbox2" name="checkbox2" />
            </div>
            <div>
              <label for="checkbox3">Volleyball</label>
              <input type="checkbox" id="checkbox3" name="checkbox3" />
            </div>
          </div>
        </div>
        <div class="inputDiv">
          <h4>Gender</h4>
          <div class="checkboxDiv">
            <div>
              <label for="radio1">Male</label>
              <input type="radio" id="radio1" name="radio" />
            </div>
            <div>
              <label for="radio2">Female</label>
              <input type="radio" id="radio2" name="radio" />
            </div>
            <div>
              <label for="radio3">Other</label>
              <input checked type="radio" id="radio3" name="radio" />
            </div>
          </div>
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
.checkboxDiv {
  display: flex;
  justify-content: space-around;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}
</style>

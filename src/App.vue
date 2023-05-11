<template>
  <div class="main">
    <div class="wrapper">
      <form class="myForm">
        <div class="inputDiv">
          <label for="nameInput">Name</label>
          <input
            v-model="user.name"
            type="text"
            id="nameInput"
            placeholder="Please enter a name"
          />
        </div>
        <div class="inputDiv">
          <label for="surnameInput">Surname</label>
          <input
            v-model="user.surname"
            type="text"
            id="surnameInput"
            placeholder="Please enter a surname"
          />
        </div>
        <div class="inputDiv">
          <label for="email">Email</label>
          <input
            v-model="user.email"
            type="email"
            id="email"
            placeholder="Please enter a email"
          />
        </div>
        <div class="inputDiv">
          <label for="country">Country</label>
          <select
            v-model="user.country"
            name="country"
            id="country"
            class="selected"
          >
            <option
              v-for="item in getCountries"
              :key="item.id"
              :value="item.id"
            >
              {{ item.name }}
            </option>
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
        <div>
          <input type="file" hidden ref="myFileInput" @change="onFileChange" />
          <button
            class="fileBtn"
            type="button"
            @click="$refs.myFileInput.click()"
          >
            Select File
          </button>
        </div>
        <button type="submit" class="submitBtn">Submit</button>
      </form>
    </div>
    <div class="wrapper">
      <p>User Info: {{ user }}</p>
      <p>{{ getCountryNameById(user.country) }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      countries: [
        { id: 1, name: "England" },
        { id: 2, name: "Germany" },
        { id: 3, name: "France" },
      ],
      user: {
        name: "",
        surname: "",
        email: "",
        country: 1,
      },
    };
  },
  methods: {
    onFileChange(e) {
      console.log(e);
    },
    getCountryNameById(id) {
      return this.getCountries.find((item) => item.id === id).name;
    },
  },
  computed: {
    getCountries() {
      return this.countries;
    },
  },
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
  gap: 10px;
}
.wrapper {
  width: 50%;
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
.fileBtn {
  border: none;
  border-radius: 5px;
  padding: 5px;
  background-color: green;
  color: white;
  cursor: pointer;
}
.fileBtn:active {
  transform: scale(0.95);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}
</style>

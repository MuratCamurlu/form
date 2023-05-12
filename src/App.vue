<template>
  <div class="main">
    <div class="wrapper">
      <form @submit.prevent="submitForm" class="myForm">
        <div class="inputDiv">
          <label for="nameInput">Name</label>
          <input
            :class="userValidations.name ? 'isError' : ''"
            v-model="user.name"
            type="text"
            id="nameInput"
            placeholder="Please enter a name"
          />
        </div>
        <div class="inputDiv">
          <label for="surnameInput">Surname</label>
          <input
            :class="userValidations.surname ? 'isError' : ''"
            v-model="user.surname"
            type="text"
            id="surnameInput"
            placeholder="Please enter a surname"
          />
        </div>
        <div class="inputDiv">
          <label for="email">Email</label>
          <input
            :class="userValidations.email ? 'isError' : ''"
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
          <textarea
            v-model="user.address"
            name="address"
            id="addressInput"
            rows="5"
          />
        </div>
        <div class="inputDiv">
          <h4>Hobbies</h4>
          <div class="checkboxDiv">
            <div v-for="item in hobbies" :key="item.id">
              <label for="checkbox1">{{ item.name }}</label>
              <input
                type="checkbox"
                id="checkbox1"
                name="checkbox1"
                :value="item.id"
                v-model="user.hobbies"
              />
            </div>
          </div>
        </div>
        <div class="inputDiv">
          <h4>Gender</h4>
          <div class="checkboxDiv">
            <div v-for="item in gender" :key="item.id">
              <label :for="item.name">{{ item.name }}</label>
              <input
                :value="item.id"
                type="radio"
                :id="item.name"
                name="radio"
                v-model="user.gender"
              />
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
            {{ file?.name ? "Change File" : "Select File" }}
          </button>
          <span v-if="file?.name">{{ file.name }}</span>
        </div>
        <div>
          <IsAccept v-model="user.isAccept" />
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
import IsAccept from "./components/isAccept.vue";

export default {
  name: "App",
  data() {
    return {
      userValidations: {
        name: false,
        surname: false,
        email: false,
      },
      file: {},
      gender: [
        { id: 1, name: "Male" },
        { id: 2, name: "Female" },
        { id: 3, name: "Other" },
      ],
      hobbies: [
        { id: 1, name: "Football" },
        { id: 2, name: "Basketball" },
        { id: 3, name: "Volleyball" },
      ],
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
        address: "",
        hobbies: [],
        gender: 3,
        file: "",
        isAccept: true,
      },
    };
  },
  methods: {
    validateData() {
      const obj = {
        name: this.user.name.trim() === "",
        surname: this.user.surname.trim() === "",
        email: this.user.email.trim() === "",
      };
      console.log(obj);
      return obj;
    },
    submitForm() {
      const validationResult = this.validateData();
      this.userValidations = validationResult;
      if (Object.values(validationResult).includes(true)) {
        alert("Form is invalid!!!");
      } else {
        this.user = {
          name: "",
          surname: "",
          email: "",
          country: 1,
          address: "",
          hobbies: [],
          gender: 3,
          file: "",
          isAccept: true,
        };
        this.file = {};
      }
    },
    onFileChange(e) {
      console.log(e.target.files);
      this.file = { name: e.target.files[0].name };
      this.user.file = {
        name: e.target.files[0].name,
        size: e.target.files[0].size,
        type: e.target.files[0].type,
      };
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
  components: { IsAccept },
};
</script>

<style>
.isError {
  border-color: red !important;
}
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

<template>
  <div style="display: flex,flexDrection:column,gap:10px;">
    <div v-for="item in userExp" :key="item.company" style="display: flex">
      <div>
        <label for="name">Company Name</label>
        <input
          v-model="userExp.company"
          type="text"
          id="name"
          placeholder="company A"
        />
      </div>
      <div>
        <label for="exp">Experience</label>
        <input
          v-model="userExp.exp"
          type="number"
          id="exp"
          placeholder="Year"
        />
      </div>
    </div>
  </div>

  <button @click="addNewExp()">Add Exp</button>
</template>
<script>
export default {
  name: "DynamicInput",
  data() {
    return {
      userExp: [
        {
          company: "",
          exp: "",
        },
      ],
    };
  },
  methods: {
    addNewExp() {
      this.userExp.push({
        company: "",
        exp: "",
      });
    },
  },
};
</script>
<style></style>

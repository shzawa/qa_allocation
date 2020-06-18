<template>
  <div>
    <form @submit.prevent="addMentor(name, rank)">
      <input type="text" v-model="name" />
      <select v-model="rank">
        <option
          v-for="(rank, index) in $parent.ranks"
          :key="index"
          :value="rank"
        >
          {{ rank }}
        </option>
      </select>
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      rank: "red"
    };
  },
  methods: {
    addMentor(name, rank) {
      if (!this.name) {
        return;
      }
      this.$emit("addMentor", { name, rank });
      this.name = "";
    }
  }
};
</script>

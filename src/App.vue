<template>
  <div id="app">
    <AddMentorForm @addMentor="addMentor" />

    <div id="lists-wrapper">
      <RankBlock
        @sortedMentor="sortedRedList"
        :rank="ranks[0]"
        :list="redList"
      />
      <RankBlock
        @sortedMentor="sortedBlueList"
        :rank="ranks[1]"
        :list="blueList"
      />
      <RankBlock
        @sortedMentor="sortedOjtList"
        :rank="ranks[2]"
        :list="ojtList"
      />
    </div>
  </div>
</template>

<script>
import RankBlock from "./components/RankBlock.vue";
import AddMentorForm from "./components/AddMentorForm.vue";

export default {
  name: "App",
  components: {
    RankBlock,
    AddMentorForm
  },
  data() {
    return {
      redList: [],
      blueList: [],
      ojtList: [],
      ranks: ["red", "blue", "ojt"]
    };
  },
  methods: {
    addMentor({ name, rank }) {
      let list = [];
      if (rank === this.ranks[0]) {
        list = this.redList;
      } else if (rank === this.ranks[1]) {
        list = this.blueList;
      } else {
        list = this.ojtList;
      }

      list.unshift({ id: list.length, name });
    },
    sortedRedList(sorted) {
      this.redList = sorted;
    },
    sortedBlueList(sorted) {
      this.blueList = sorted;
    },
    sortedOjtList(sorted) {
      this.ojtList = sorted;
    }

    // list.sort((a, b) => a.id - b.id);
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#lists-wrapper {
  display: flex;
  justify-content: center;
}
</style>

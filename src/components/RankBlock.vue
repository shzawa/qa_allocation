<template>
  <div class="list-wrapper" :id="rank">
    <h2>
      {{ rank }}
    </h2>

    <div v-for="(mentor, index) in list" :key="index">
      {{ mentor.id }}
      <button @click="sorting(mentor)" class="btn-square-shadow">
        {{ mentor.name }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    rank: String,
    list: Array
  },
  methods: {
    sorting(mentor) {
      const sorted = this.list.filter(
        listMentor => listMentor.id !== mentor.id
      );
      sorted.push(mentor);
      this.$emit(`sortedMentor`, sorted);
    }
  }
};
</script>

<style scoped>
.list-wrapper {
  width: 30%;
}
.list-wrapper div {
  margin-bottom: 1rem;
}

#red h2 {
  color: #ff7c5c;
}
#red .btn-square-shadow {
  border: 0px;
  display: inline-block;
  padding: 0.5em 1em;
  text-decoration: none;
  background: #f7f7f7;
  border-left: solid 6px #ff7c5c; /*左線*/
  color: #ff7c5c; /*文字色*/
  font-weight: bold;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.29);
}
#red .btn-square-shadow:active {
  box-shadow: inset 0 0 2px rgba(128, 128, 128, 0.1);
  transform: translateY(2px);
}

#blue h2 {
  color: #5c90ff;
}
#blue .btn-square-shadow {
  border: 0px;
  display: inline-block;
  padding: 0.5em 1em;
  text-decoration: none;
  background: #f7f7f7;
  border-left: solid 6px #5c90ff; /*左線*/
  color: #5c90ff; /*文字色*/
  font-weight: bold;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.29);
}
#blue .btn-square-shadow:active {
  box-shadow: inset 0 0 2px rgba(128, 128, 128, 0.1);
  transform: translateY(2px);
}

#ojt h2 {
  color: #50c059;
}
#ojt .btn-square-shadow {
  border: 0px;
  display: inline-block;
  padding: 0.5em 1em;
  text-decoration: none;
  background: #f7f7f7;
  border-left: solid 6px #50c059; /*左線*/
  color: #50c059; /*文字色*/
  font-weight: bold;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.29);
}
#ojt .btn-square-shadow:active {
  box-shadow: inset 0 0 2px rgba(128, 128, 128, 0.1);
  transform: translateY(2px);
}
</style>

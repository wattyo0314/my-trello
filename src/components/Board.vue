<template>
  <div>
    <header>my-trello</header>
    <main>
      <p class="info-line">ALL: {{ totalCardCount }} tasks</p>
      <div class="list-index">
        <list
          v-for="(item, index) in lists"
          :key="item.id"
          :title="item.title"
          :cards="item.cards"
          :listIndex="index"
        ></list>
        <list-add />
      </div>
    </main>
  </div>
</template>

<script>
import ListAdd from "./ListAdd";
import List from "./List";
import { mapState } from "vuex";
export default {
  components: {
    ListAdd,
    List,
  },
  computed: {
    ...mapState(["lists"]),
  },
};
</script>
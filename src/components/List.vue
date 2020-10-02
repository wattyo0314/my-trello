<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}</p>
      <p class="total-counter">Total:{{ totalCardInList }}</p>
      <div class="deletelist" @click="removeList">×</div>
    </div>
    <card
      v-for="(item, index) in cards"
      :key="item.id"
      :body="item.body"
      :listIndex="listIndex"
      :cardIndex="index"
    ></card>
    <card-add :listIndex="listIndex" />
  </div>
</template>

<script>
import CardAdd from "./CardAdd";
import Card from "./Card";
export default {
  components: {
    CardAdd,
    Card,
  },
  props: {
    title: {
      type: String,
      required: true,
    },
    listIndex: {
      type: Number,
      required: true,
    },
    cards: {
      type: Array,
      required: true,
    },
  },
  methods: {
    removeList: function () {
      if (confirm("このリストを本当に削除していいですか？")) {
        this.$store.dispatch("removelist", { listIndex: this.listIndex });
      }
    },
  },
  computed: {
    totalCardInList() {
      return this.cards.length;
    },
  },
};
</script>

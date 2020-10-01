<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}</p>
      <div class="deletelist" @click="removeList">×</div>
    </div>
    <card-add :listIndex="listIndex" />
  </div>
</template>

<script>
import CardAdd from './CardAdd'
export default {
  components: {
    CardAdd
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
  },
  methods: {
    removeList: function () {
      if (confirm("このリストを本当に削除していいですか？")) {
        this.$store.dispatch("removelist", { listIndex: this.listIndex });
      }
    },
  },
};
</script>

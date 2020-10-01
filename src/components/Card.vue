<template>
  <div class="card">
    <button class="closeButton" @click="removeCardFromList">×</button>
    <div class="body">
      {{ body }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    body: {
      style: String,
      required: true,
    },
    listIndex: {
      style: Number,
      required: true,
    },
    cardIndex: {
      style: Number,
      required: true,
    },
  },
  methods: {
    removeCardFromList: function() {
      if (confirm("本当にこのカードを削除しますか？")) {
        this.$store.dispatch("removeCardFromList", {
          cardIndex: this.cardIndex,
          listIndex: this.listIndex,
        });
      }
    },
  },
};
</script>

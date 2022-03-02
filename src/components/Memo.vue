<template>
  <li class="memo">
    <div class="memo__checkbox">
      <input type="checkbox" />
    </div>
    <div class="memo__text">{{ memo.text }}</div>
    <button class="memo__delete" @click="send(memo.id)">削除</button>
  </li>
</template>

<script>
export default {
  props: {
    memo: {
      type: Object,
      required: true,
    },
  },
  methods: {
    send(id) {
      this.$emit("my-click", id)
    },
  },
}
</script>

<style scoped>
.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #b23b61;
}

.memo__text {
  margin-left: 2rem;
  text-align: left;
}

.memo__text--done {
  text-decoration-line: line-through;
}

.memo__delete {
  margin-left: 1rem;
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.memo__delete:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}
</style>

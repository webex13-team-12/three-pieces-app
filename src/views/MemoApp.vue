<template>
  <h1>Vue メモ</h1>
  <div class="memo-list">
    <ul class="memo-list__container">
      <Memo
        v-for="memo in memos"
        v-bind:key="memo.id"
        v-bind:memo="memo"
        @my-click="reflectNum"
      />
    </ul>
    <div class="add-memo-field">
      <input class="add-memo-field__input" type="text" v-model="inputMemo" />
      <button v-on:click="addMemo" class="add-memo-field__button">追加</button>
    </div>
  </div>
</template>

<script>
import Memo from "@/components/Memo.vue"
export default {
  components: { Memo },
  data() {
    return {
      memos: [],
      inputMemo: "",
    }
  },
  methods: {
    addMemo() {
      let memo = { id: this.memos.length, text: this.inputMemo }
      this.inputMemo = ""
      this.memos.push(memo)
    },
    reflectNum(id) {
      this.memos.splice(id, 1)
    },
  },
}
</script>

<style scoped>
.memo-list {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
}

.memo-list__container {
  padding: 0;
}

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

.add-memo-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.add-memo-field__input {
  padding: 10px;
}
.add-memo-field__button {
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.add-memo-field__button:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}
</style>

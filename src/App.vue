<template>
  <div class="wrapper">
    <div v-if="posts.length !== 0" class="card" v-for="item in posts" :key="item.id">
      <div>
        <p class="title">
          <strong>
            Название:
          </strong>
          {{ item.title }}
        </p>
        <p class="subtitle">
          <strong>
            Описание:
          </strong>
          {{ item.body }}
        </p>
      </div>
      <div>
        <button @click="removePost(item.id)" class="btn">Удалить</button>
      </div>
    </div>
    <div v-else class="wrapper-err">
      <span>Пользователи не найдены</span>
    </div>
    <div class="wrapper-btn">
      <button @click="clickHandler" class="btn">Получить посты</button>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      count: 0,
      posts: []
    }
  },
  methods: {
    clickHandler() {
      (async () => {
        const { data } = await axios.get("https://jsonplaceholder.typicode.com/posts")
        this.posts = data
      })()
    },
    removePost(id) {
      this.posts = this.posts.filter(item => item.id !== id)
    }
  }
}
</script>
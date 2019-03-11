<template>
  <ion-app>
    <ion-header>
      <ion-toolbar color="danger">
        <ion-title>S C A R Y T O D O S</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <ion-list v-if="todos.length > 0">
        <ion-item v-for="todo in todos" :key="todo.id">
          <ion-label>{{todo.title}}</ion-label>
        </ion-item>
      </ion-list>
      <ion-list v-else>
        <ion-item v-for="i in 20" :key="i">
          <ion-label>
            <ion-skeleton-text animated>
            </ion-skeleton-text>
          </ion-label>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-app>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      todos: []
    }
  },
  created() {
    setTimeout(
      () => (
        this.getDataFromAPI()
        ), 3000)
  },
  methods: {
    async getDataFromAPI() {
      try {
        const req = await fetch('https://jsonplaceholder.typicode.com/todos')
        this.todos = await req.json()
      }
      catch(e) {
        console.error(`Error: ${e}`)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>

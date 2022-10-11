<script>
export default {
  data() {
    return {
      notifications: [
        { id: 0, pseudo: 'Marc', notificationSort: 'a commenté', isRead: false },
        { id: 1, pseudo: 'Elise', notificationSort: 'a publié', isRead: false }
      ]
    }
  },
  methods: {
    allReaded() {
      let tempNotifications = this.notifications

      tempNotifications = tempNotifications.map((item) => {
        return {
          id: item.id,
          pseudo: item.pseudo,
          notificationSort: item.notificationSort,
          isRead: true
        }
      })

      console.log(tempNotifications);
      this.notifications = tempNotifications
    }
  }
}
</script>

<template>
  <div class="greetings">
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <h2>Salut vuejs</h2>
    <button v-on:click="allReaded">Supprimer les notifications lu</button>

    <ul>
      <li v-for="notification in notifications" :key="notification.id"
        v-on:click="notification.isRead = !notification.isRead" :class="{ active: notification.isRead }">
        {{notification.pseudo}} -
        {{notification.notificationSort}} - {{notification.isRead}}</li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

li {
  &.active {
    color: red;
  }
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>

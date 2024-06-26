template>
  <div>
    <h1>Users</h1>
    <ul v-if="users.length">
      <li v-for="user in users" :key="user.id">
        {{ user.firstName }} {{ user.lastName }} -
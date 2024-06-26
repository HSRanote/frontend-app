<template>
  <div>
    <h1>User List</h1>
    <ul>
      <li v-for="user in users" :key="user.id">{{ user.firstName }} {{ user.lastName }} - {{ user.email }}</li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
import axios from 'axios';

export default defineComponent({
  name: 'UserList',
  setup() {
    const users = ref([]);

    const fetchUsers = async () => {
      try {
        const response = await axios.get('http://localhost:3000/users');
        users.value = response.data;
      } catch (error) {
        console.error('Error fetching users:', error);
      }
    };

    onMounted(fetchUsers);

    return {
      users    };
  },
});
</script>

<style scoped>
h1 {
  font-size: 2em;
  margin-bottom: 0.5em;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  padding: 0.5em 0;
}
</style>

<template>
  <div>
    <h1>Áreas</h1>
    <ul>
      <li v-for="user in users" >
        {{ user.name }}
      </li>
    </ul>
  </div>
</template>

<script>

  export default {
    name: "Area",
    data() {
      return {
        users: [],
      }
    },
    mounted() {
      this.getUsers();  
    },
    
    methods: {
      getUsers() {
        this.$axios.get('/users/list')
          .then((response) => {
            this.users = response.data;            
          })
          .catch((error) => {
            console.log(error);
          })
      },
      handleClick(id) {
      console.log('Usuario clicado:', id)
    }
    }
  }
</script>
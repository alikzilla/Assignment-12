<template>
  <div>
    <div class="profile">
      <img :src="user.profilePicture" alt="Profile Picture" class="profile-picture">
      <div class="user-details">
        <h1>{{ user.name }}</h1>
        <p>Email: {{ user.email }}</p>
        <p v-if="user.isAdmin">Admin</p>
        <p v-else>Regular User</p>
        <p>Age: {{ userAge }} years</p>
      </div>
    </div>

    <div class="edit-profile">
      <h2>Edit Profile</h2>
      <form @submit.prevent="updateProfile">
        <label for="name">Name:</label>
        <input type="text" v-model="user.name" id="name">

        <label for="email">Email:</label>
        <input type="email" v-model="user.email" id="email">

        <label for="isAdmin">Admin:</label>
        <input type="checkbox" v-model="user.isAdmin" id="isAdmin">

        <label for="birthdate">Birthdate:</label>
        <input type="date" v-model="user.birthdate" id="birthdate">

        <label for="profilePicture">Profile Picture URL:</label>
        <input type="text" v-model="user.profilePicture" id="profilePicture">

        <button type="submit">Update Profile</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: 'Alikhan Nuspekov',
        email: 'nuspek@example.com',
        profilePicture: 'https://avatars.githubusercontent.com/u/118796959?v=4',
        isAdmin: false,
        birthdate: '2005-06-16',
      },
    };
  },
  computed: {
    userAge() {
      const birthdate = new Date(this.user.birthdate);
      const today = new Date();
      return today.getFullYear() - birthdate.getFullYear();
    },
  },
  methods: {
    updateProfile() {
      console.log('Profile Updated:', this.user);
    },
  },
  watch: {
    user: {
      handler(newValue, oldValue) {
        console.log('User details modified:', newValue);
      },
      deep: true,
    },
  },
  created() {
    console.log('User Profile Component Created');
  },
};
</script>

<style scoped>
.profile {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.profile-picture {
  border-radius: 50%;
  margin-right: 20px;
}

.user-details {
  max-width: 400px;
}

.edit-profile {
  margin-top: 30px;
}

form {
  display: grid;
  grid-template-columns: 1fr 3fr;
  grid-gap: 10px;
}

label {
  font-weight: bold;
}

button {
  grid-column: span 2;
  padding: 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>

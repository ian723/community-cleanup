<template>
  <div>
    <header class="header">
      <h1>User Profile</h1>
    </header>
    <div class="container">
      <div class="profile-header">
        <img src="images/user_profile.jpg" alt="User Profile Picture" />
        <h1>{{ user.username }}</h1>
      </div>
      <section class="profile-section">
        <h2>Profile Information</h2>
        <p>
          <strong>Email:</strong> <span>{{ user.email }}</span>
        </p>
        <p>
          <strong>Phone:</strong> <span>{{ user.phone }}</span>
        </p>
        <p>
          <strong>Address:</strong> <span>{{ user.address }}</span>
        </p>
      </section>
      <section class="profile-section">
        <h2>Recent Activities</h2>
        <ul>
          <li v-for="activity in user.recentActivities" :key="activity">
            {{ activity }}
          </li>
        </ul>
      </section>
      <section class="profile-section">
        <h2>Update Profile</h2>
        <form @submit.prevent="updateProfile" class="update-form">
          <div class="form-group">
            <label for="profile-picture">Profile Picture:</label>
            <input type="file" id="profile-picture" name="profile-picture" />
          </div>
          <div class="form-group">
            <label for="phone">Phone:</label>
            <input type="tel" id="phone-input" v-model="user.phone" />
          </div>
          <div class="form-group">
            <label for="address">Address:</label>
            <textarea id="address-input" v-model="user.address"></textarea>
          </div>
          <button type="submit" class="btn">Update Profile</button>
        </form>
      </section>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";

export default {
  setup() {
    const user = ref({
      username: "",
      email: "",
      phone: "",
      address: "",
      recentActivities: [],
    });

    const fetchUserProfile = () => {
      fetch("/users/profile", {
        method: "GET",
        credentials: "include",
      })
        .then((response) => response.json())
        .then((data) => {
          user.value = data;
        });
    };

    const updateProfile = () => {
      const { phone, address } = user.value;
      fetch("/users/profile", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({ phone, address }),
        credentials: "include",
      })
        .then((response) => response.json())
        .then((data) => {
          if (data.success) {
            alert("Profile updated successfully!");
          } else {
            alert("Error updating profile");
          }
        });
    };

    onMounted(() => {
      fetchUserProfile();
    });

    return {
      user,
      updateProfile,
    };
  },
};
</script>

<style scoped>
body {
  font-family: "Arial", sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
  color: #333;
}
.header {
  background-color: #4caf50;
  color: white;
  padding: 1em 0;
  text-align: center;
}
.container {
  width: 90%;
  max-width: 1200px;
  margin: 2em auto;
  padding: 0 1em;
}
.profile-header {
  text-align: center;
  margin-bottom: 2em;
}
.profile-header img {
  border-radius: 50%;
  width: 150px;
  height: 150px;
  border: 4px solid #4caf50;
  object-fit: cover;
}
.profile-header h1 {
  margin-top: 1em;
  color: #4caf50;
}
.profile-section {
  background: white;
  padding: 2em;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 2em;
}
.profile-section h2 {
  margin-top: 0;
}
.profile-section p {
  line-height: 1.6;
  margin-bottom: 1em;
}
.profile-section label {
  display: block;
  margin: 1em 0 0.5em;
}
.profile-section input,
.profile-section textarea {
  width: 100%;
  padding: 0.75em;
  font-size: 1em;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
.profile-section textarea {
  resize: vertical;
  height: 120px;
}
.update-form .form-group {
  margin-bottom: 1.5em;
}
.btn {
  display: inline-block;
  padding: 0.75em 1.5em;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1em;
  transition: background-color 0.3s ease;
}
.btn:hover {
  background-color: #45a049;
}

</style>

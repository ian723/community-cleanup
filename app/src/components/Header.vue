<template>
  <div>
    <nav>
      <div class="logo">
        <img
          src="https://i.pinimg.com/236x/8f/58/10/8f581097eab9e4a477266b7183aed867.jpg"
          alt="Logo"
        />
      </div>
      <ul>
        <li>
          <router-link to="/" exact-active-class="active">Home</router-link>
        </li>
        <li>
          <router-link to="/dashboard" exact-active-class="active"
            >Dashboard</router-link
          >
        </li>
        <li>
          <router-link to="/about-us" exact-active-class="active"
            >About Us</router-link
          >
        </li>
        <li>
          <router-link to="/gallery" exact-active-class="active"
            >Gallery</router-link
          >
        </li>
        <li>
          <router-link to="/contact-us" exact-active-class="active"
            >Contact Us</router-link
          >
        </li>
        <li class="/profile">
          <router-link to="/profile" exact-active-class="active"
            >Profile</router-link
          >
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style lang="scss" scoped>
body {
  font-family: "Times New Roman", Times, serif, sans-serif;
}

nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #ffffff; /* Change to your desired background color */
  padding: 10px 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  height: 60px; /* Adjusted height for better spacing */
}

.logo img {
  height: 50px; /* Adjusted logo size */
}

ul {
  list-style: none;
  display: flex;
  margin: 0;
  padding: 0;
  gap: 20px; /* Adds space between each list item */
}

ul li {
  display: inline-block;
}

ul li a,
ul li router-link {
  text-decoration: none;
  color: #333333; /* Adjust text color */
  padding: 10px 15px;
  position: relative;
  transition: color 0.3s ease, background-color 0.3s ease; /* Smooth transition effects */
  border-radius: 5px; /* Slightly rounded corners */
}

ul li a:hover,
ul li router-link:hover {
  background-color: #f0f0f0; /* Background color on hover */
  color: #000000; /* Text color on hover */
}

ul li .active {
  background-color: #e0e0e0; /* Background color for active link */
  color: #000000;
}

ul li .active::after {
  content: "";
  display: block;
  width: 100%;
  height: 2px;
  background-color: red;
  position: absolute;
  bottom: -5px;
  left: 0;
}

div {
  padding: 20px;
  margin: 20px 0;
  border: 1px solid #ccc;
}
</style>

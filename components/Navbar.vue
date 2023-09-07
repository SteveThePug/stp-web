<template>
    <ul class="navbar">
        <li class="left"><router-link to="/information">Information</router-link></li>
        <li class="left"><router-link to="/projects">Projects</router-link></li>
        <li class="right"><router-link to="/all-purpose">All Purpose</router-link></li>
    </ul>
</template>

<script>
export default {};
</script>
<style scoped>
.navbar {
    position: fixed;
    font-variation-settings: "ital" 0;
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    width: 100vw;
    z-index: 1;
}

.navbar li {
    float: left;
    margin: 0px 20px 20px 20px;
    font-family: "APMono", sans-serif;
    font-variation-settings: "ital" 0, "opsz" 0, "unkn" 0;
}

.navbar li.right {
    float: right;
    font-family: "APOrienteer", sans-serif;
    font-variation-settings: "wght" 0;
}

.navbar li {
    display: block;
    color: black;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 2vw;
    /* Initial value */
    transition: background-color 1s ease, font-variation-settings 1s ease-in-out;
}

a,
a:visited,
a:hover,
a:active {
    color: inherit;
    text-decoration: none;
}

.navbar li.left:hover {
    font-variation-settings: "ital" 20, "opsz" 10, "unkn" 70;
}


.navbar li.right:hover {
    font-variation-settings: "wght" 100;
}
</style>

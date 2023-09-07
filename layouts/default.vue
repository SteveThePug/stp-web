<template>
    <div class="outer navbar"></div>
    <div class="document">
        <slot />
    </div>
    <div class="outer bar-leftbox"></div>
    <div class="outer bar-rightbox"></div>
    <div class="outer bar-footer"></div>
</template>

<script>
export default {};
</script>
<style scoped>
/** New css */
.outer {
    position: fixed;
    font-variation-settings: "ital" 0;
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    z-index: 1;
    background-image: url("img/squares.gif");
    background-repeat: repeat;
    background-size: 5vw;
}

.navbar {
    left: 0vw;
    top: 0vh;
    width: 100vw;
    height: 10vh;
    clip-path: polygon(0% 0%, 100% 0%, 100% 50%, 10% 50%, 5% 100%, 0% 100%);
}

.bar-leftbox {
    left: 0vw;
    top: 10vh;
    height: 90vh;
    width: 5vw;
}

.bar-rightbox {
    left: 95vw;
    top: 5vh;
    height: 95vh;
    width: 5vw;
}

.bar-footer {
    left: 5vw;
    top: 95vh;
    height: 5vh;
    width: 90vw;
}


.document {
    position: fixed;
    left: 10vw;
    top: 10vw;
    right: 90vw;
    bottom: 90vw;
}


/** Old css */
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

.navbar li.left:hover {
    font-variation-settings: "ital" 20, "opsz" 10, "unkn" 70;
}


.navbar li.right:hover {
    font-variation-settings: "wght" 100;
}
</style>
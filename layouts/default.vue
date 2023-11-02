<template>
    <svg v-for="(circle, index) in circles" :key="index" class="circle" width="2.5vh" height="2.5vh"
        :style="{ animationDelay: circleDelays(index) + 's', animationDuration: duration + 's', fill: getFillColor(index) }">
        <rect width="100%" height="100%"></rect>
    </svg>

    <div class="outer navbar"></div>
    <div class="document">
        <slot />
    </div>
    <div class="outer bar-leftbox"></div>
    <div class="outer bar-rightbox"></div>
    <div class="outer bar-footer"></div>
</template>

<script>
export default {
    data() {
        return {
            circles: 100, // Number of circles
            duration: 10,
        };
    },
    computed: {
    },
    methods: {
        circleDelays(index) {
            // Calculate delay for each circle based on the animation duration
            return (index / this.circles) * this.duration;
        },
        getFillColor(index) {
            // Calculate fill color based on the index
            const red = (index + 20) * 10 % 255;
            const green = index * 20 % 255;
            const blue = index * 25.5 % 255;

            return `rgb(${red}, ${green}, ${blue})`;
        },
    },
};
</script>


<style>
:root {
    --right: calc(100vw - 2.5vh);
}

.circle {
    z-index: 2;
    position: fixed;
    animation: circleLoop infinite;
    animation-timing-function: linear;
    left: 0;
    top: 0;
}

@keyframes circleLoop {
    0% {
        left: 0;
        top: 0
    }

    25% {
        left: var(--right);
        top: 0;
    }

    50% {
        left: var(--right);
        top: 97.5vh;
    }

    75% {
        left: 0;
        top: 97.5vh;
    }

    100% {
        left: 0;
        top: 0;
    }
}

.outer {
    position: fixed;
    font-variation-settings: "ital" 0;
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    z-index: 1;
    background-color: aqua;
    background-repeat: repeat;
    background-size: 10vw;
}

.navbar {
    left: 0vw;
    top: 0vh;
    width: 100vw;
    height: 5vh;
    clip-path: polygon(0vw 0vh, 100vw 0vh, 100vw 2.5vh, 5vh 2.5vh, 2.5vh 5vh, 0vw 5vh);
}

.bar-leftbox {
    left: 0vw;
    top: 5vh;
    height: 92.5vh;
    width: 2.5vh;
}

.bar-rightbox {
    left: calc(100vw - 2.5vh);
    top: 2.5vh;
    height: 92.5vh;
    width: 2.5vh;
}

.bar-footer {
    left: 0vw;
    top: 95vh;
    height: 5vh;
    width: 100vw;
    clip-path: polygon(0vw 0vh, 100vw 0vh, 100vw 2.5vh, 5vh 2.5vh, 2.5vh 5vh, 0vw 5vh);
    transform: rotate(180deg);
}

.document {
    position: fixed;
    left: 2.5vh;
    top: 2.5vh;
    width: calc(100vw - 5vh);
    height: 95vh;
    overflow-y: scroll;
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
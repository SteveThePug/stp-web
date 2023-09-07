<template>
    <div class="body">
    </div>
</template>
  
<style scoped>
.body {
    margin: 0px 0px 0px 0px;
    width: 100vw;
    height: 100vh;
    background-image: url("/img/community.jpg");
    background-size: 20vw;
    background-repeat: repeat;
    transition: background-image 1s ease;
}
</style>

<script>
export default {
    data() {
        let sources = ["b&w.jpg", "chance.jpg", "community.jpg", "cone.png", "daniel.png", "lean.jpg", "monopoly.jpg", "perfect.jpg"]
        return {
            sources,
            currentSourceIndex: 0
        }
    },
    mounted() {
        this.changeBackgroundImage(); // Call the function when the component is mounted
        setInterval(this.changeBackgroundImage, 1000); // Change image every 1000ms

    },
    methods: {
        changeBackgroundImage() {
            this.currentSourceIndex = (this.currentSourceIndex + 1) % this.sources.length;
            const newImageSource = `/img/${this.sources[this.currentSourceIndex]}`;
            this.$el.style.backgroundImage = `url("${newImageSource}")`;
        }
    }
}
</script>
    
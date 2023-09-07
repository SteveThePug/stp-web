<template>
    <div>
        <img v-for="(imageSrc, index) in imageSources " :key="imageSrc" :src="imageSrc" @mousedown="select(index)"
            :style="getImageStyle(index)" alt=" Image" />
    </div>
</template>

<style scoped> div {
     width: 100vw;
     height: 100vh;
     overflow: hidden;
 }
</style>
<script>

export default {
    data() {
        let size = 10;

        let sources = [];
        for (let i = 1; i < 7; i++) {
            sources.push(`/img/${i}.jpg`)
        }

        let positions = []; {
            sources.forEach((source, index) => {
                positions.push({
                    top: Math.random() * 100,
                    left: `-${size}`
                })
            })
        }


        return {
            imageSources: sources,
            numSources: sources.length,
            size: size,
            positions: positions,
            selected: null,
            interval: 4000
        };
    },
    mounted() {
        this.positions.forEach((position, index) => {
            if (this.selected) return;
            let timeout = setTimeout(() => {
                if (this.selected) {
                    clearTimeout(timeout);
                    return;
                }
                this.transtion(index);
                this.loop(index);
            }, index * 1000)
        })
    },
    methods: {
        transtion(index) {
            this.positions[index] = {
                top: Math.random() * 100,
                left: (this.positions[index].left > 50) ? `-${this.size}` : 100
            }
        },
        center(index) {
            this.positions[index] = {
                top: Math.random() * 100,
                left: 50 - this.size / 2
            }
        },
        loop(index) {
            let interval = setInterval(() => {
                if (this.selected) {
                    clearInterval(interval);
                    return;
                }
                this.transtion(index);
            }, this.interval)
        },
        select(index) {
            this.selected = index;
            this.center(index)
        },
        getImageStyle(index) {
            return {
                width: `${this.size}dvw`,
                height: `${this.size}dvw`,
                position: "absolute",
                top: `${this.positions[index].top}dvh` || "0",
                left: `${this.positions[index].left}dvw` || "0",
                transition: `all ${this.interval}ms ease`,
                opacity: (this.selected == index || !this.selected) ? 1 : 0
            };
        }
    }
}
</script>
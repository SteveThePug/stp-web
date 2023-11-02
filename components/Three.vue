<template>
    <canvas ref="experience" />
</template>
<style scoped>
canvas {
    left: 0px;
    top: 0px;
    z-index: 0;
    overflow: hidden;
}
</style>

<script setup>
import * as THREE from 'three';
import { onMounted, ref } from 'vue';
import { useElementSize, useParentElement } from '@vueuse/core'
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js'

let renderer;
const experience = ref(null);
const parent = useParentElement(experience);
const { width, height } = useElementSize(parent);
const aspectRatio = computed(() => width.value / height.value)

const scene = new THREE.Scene()

const camera = new THREE.PerspectiveCamera(75, aspectRatio.value, 0.1, 1000)
camera.position.set(0, 0, 3)
scene.add(camera)

const light = new THREE.PointLight(0xff00ff, 1000, 1000)
light.position.set(-1, -1, -1);
scene.add(light);


const light2 = new THREE.PointLight(0xff0000, 1000, 1000)
light2.position.set(1, 1, 1);
scene.add(light2);

let box;
const gltfLoader = new GLTFLoader();
gltfLoader.load('/glb/box.glb', gltf => {
    gltf.scene.scale.set(10, 10, 10);
    box = gltf.scene;
    box.rotation.y = -1.8;
    box.position.y = - 0.5;
    box.position.z = .2;
    scene.add(box);
})


function updateCamera() {
    camera.aspect = aspectRatio.value
    camera.updateProjectionMatrix()
}

function updateRenderer() {
    renderer.setSize(width.value, height.value)
    renderer.render(scene, camera)
}

function setRenderer() {
    if (experience.value) {
        renderer = new THREE.WebGLRenderer({ canvas: experience.value, alpha: true, powerPreference: "low-power", preserveDrawingBuffer: true, antialias: false })
    }
}

watch(aspectRatio, () => {
    updateCamera()
    updateRenderer()
})

onMounted(() => {
    setRenderer()
    loop()
})

let time = 0;
let count = 0;
const loop = () => {
    time += 0.05;

    count++;

    if (box) {
        box.rotation.x = 0.2 * Math.cos(0.5 * time);
        box.rotation.y = 0.2 * Math.sin(0.2 * time) - 1.5;
        box.position.x = 0.2 * Math.sin(0.1 * time);
    }

    updateRenderer()
    requestAnimationFrame(loop);
}
</script>

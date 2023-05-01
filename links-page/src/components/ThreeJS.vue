<template>
  <div id="container"></div>
</template>

<script>
import * as THREE from "three";
import { OrbitControls } from "three/addons/controls/OrbitControls.js";
import { Water } from "three/addons/objects/Water.js";
import { Sky } from "three/addons/objects/Sky.js";
import { OBJLoader } from 'three/examples/jsm/loaders/OBJLoader.js';

import lilacRustImg from '../assets/textures/lilacrustpfimage.jpg'
import waterTexture from '../assets/textures/waternormals.jpg';
//import boatModel from '../assets/models/Boat.obj'
//import eyeballModel from '../assets/models/Eye_Sphere.fbx'

let container;
let camera, scene, renderer;
let controls, water, sun, mesh, mesh2;
let skyUniforms;
let add = true;

window.onload = () => {
  init();
  animate();
}

function loadModel(objURL, meshMaterial) {
  let loader = new OBJLoader();
  loader.load(objURL, function ( object ) {
    pouch = new THREE.Mesh(
      object.children[0].geometry,
      new THREE.MeshStandardMaterial(meshMaterial)
    );
    scene.add(pouch);

    if (!object.children[1]) {
      return;
    }
  
    hangHole = new THREE.Mesh(
      object.children[1].geometry,
      new THREE.MeshStandardMaterial({
        color: 0xffffff,
      })
    );
    scene.add(hangHole);
  });
}

function init() {
  container = document.getElementById("container");

  //

  renderer = new THREE.WebGLRenderer();
  renderer.setPixelRatio(window.devicePixelRatio);
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.toneMapping = THREE.ACESFilmicToneMapping;
  container.appendChild(renderer.domElement);

  //

  scene = new THREE.Scene();

  camera = new THREE.PerspectiveCamera(
    55,
    window.innerWidth / window.innerHeight,
    1,
    20000
  );
  camera.position.set(60, 30, 100);

  const ambientLight = new THREE.AmbientLight(0xffffff, .6);
  scene.add(ambientLight);

  //

  sun = new THREE.Vector3();

  // Water

  const waterGeometry = new THREE.PlaneGeometry(10000, 10000);

  water = new Water(waterGeometry, {
    textureWidth: 512,
    textureHeight: 512,
    waterNormals: new THREE.TextureLoader().load(
      waterTexture,
      function (texture) {
        texture.wrapS = texture.wrapT = THREE.RepeatWrapping;
      }
    ),
    sunDirection: new THREE.Vector3(),
    sunColor: 0xffffff,
    waterColor: 0x001e0f,
    distortionScale: 3.7,
    fog: scene.fog !== undefined,
  });

  water.rotation.x = -Math.PI / 2;

  scene.add(water);

  // Skybox

  const sky = new Sky();
  sky.scale.setScalar(10000);
  scene.add(sky);

  skyUniforms = sky.material.uniforms;

  skyUniforms["turbidity"].value = .05;
  skyUniforms["rayleigh"].value = 0;
  skyUniforms["mieCoefficient"].value = 0.005;
  skyUniforms["mieDirectionalG"].value = 0.8;

  const parameters = {
    elevation: 2,
    azimuth: 180,
  };

  const pmremGenerator = new THREE.PMREMGenerator(renderer);
  let renderTarget;

  function updateSun() {
    const phi = THREE.MathUtils.degToRad(90 - parameters.elevation);
    const theta = THREE.MathUtils.degToRad(parameters.azimuth);

    sun.setFromSphericalCoords(1, phi, theta);

    sky.material.uniforms["sunPosition"].value.copy(sun);
    water.material.uniforms["sunDirection"].value.copy(sun).normalize();

    if (renderTarget !== undefined) renderTarget.dispose();

    renderTarget = pmremGenerator.fromScene(sky);

    scene.environment = renderTarget.texture;
  }

  updateSun();

  //

  const geometry = new THREE.BoxGeometry(30, 30, 30);
  let texture = new THREE.TextureLoader().load(lilacRustImg);
  const material = new THREE.MeshStandardMaterial({map: texture});

  mesh = new THREE.Mesh(geometry, material);
  mesh.position.y = 30;
  mesh.name = "GoogleDriveCube";
  scene.add(mesh);

  camera.position.x = camera.position.x + 1;
  camera.updateProjectionMatrix();

  //

  controls = new OrbitControls(camera, renderer.domElement);
  controls.maxPolarAngle = Math.PI * 0.495;
  controls.target.set(0, 10, 0);
  controls.minDistance = 40.0;
  controls.maxDistance = 200.0;
  controls.autoRotate = true;
  controls.enabled = false;
  controls.update();

  //loadModel(boatModel, {color: 0x000000});
  

  window.addEventListener("resize", onWindowResize);
}

function onWindowResize() {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();

  renderer.setSize(window.innerWidth, window.innerHeight);
}

function animate() {
  requestAnimationFrame(animate);
  render();
}

function render() {
  const time = performance.now() * 0.001;

  mesh.rotation.x = time * 0.5;
  mesh.rotation.z = time * 0.51;

  water.material.uniforms["time"].value += 1.0 / 60.0;

  if (skyUniforms["turbidity"].value > .1) {
    add = false;
  } else if (skyUniforms["turbidity"].value < .05) {
    add = true;
  }

  if (add) {
    skyUniforms["turbidity"].value = skyUniforms["turbidity"].value + .00025;
  } else {
    skyUniforms["turbidity"].value = skyUniforms["turbidity"].value - .00025;
  }

  //controls.update();

  renderer.render(scene, camera);
}
</script>

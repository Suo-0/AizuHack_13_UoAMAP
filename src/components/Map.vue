<template>
  <div>
    <div id="map" @click="addPin($event)" style = "margin : 0 auto">
      <div v-for="(pin, index) in pins" :key="index" 
           class="pin" :style="{ left: pin.x + 'px', top: pin.y + 'px' }">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pins: [],  
    };
  },
  methods: {
    addPin(event) {

      const mapElement = document.getElementById('map');
      const rect = mapElement.getBoundingClientRect();
      const x = event.clientX - rect.left;
      const y = event.clientY - rect.top;

      this.pins = [{ x, y }];
    },
  },
};
</script>

<style>
#map {
  position: relative;
  width: 1100px;  
  height: 1000px;  
  background-image: url("../assets/image/zentai.jpg");  
  background-repeat: no-repeat;
  background-size: cover;
  cursor: crosshair;
}

.pin {
  width: 30px;  
  height: 30px;  
  background-image: url("../assets/image/pin.png");  
  background-size: cover;
  position: absolute; 
  transform: translate(-50%, -50%); 
}
</style>
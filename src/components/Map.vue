<template>
  <div>
    <div class="q-pa-md q-gutter-sm">


      <q-dialog v-model="icon">
        <q-card style="width: 820px; max-width: 100vw;" id="img-card">
          <div class="my-dialog-content">
            <div id="map" @mousemove="logMousePosition" @click="addPin" style="margin: 0 auto" ref="map">
              <img src="../assets/image/zentai.jpg" class="map_image">
              <div v-for=" (pin, index) in pins" :key="index" class="pin"
                :style="{ left: pin.x + 'px', top: pin.y + 'px' }">
                <span class="pin-label">{{ roomname }}, {{ roomdescription }}</span>
              </div>
            </div>
            <div class="image-container">
              <div id="screen-log" class="log-container">
                Screen X/Y: {{ screenX }}, {{ screenY }}
                Client X/Y: {{ clientX }}, {{ clientY }}
                Pin X/Y: {{ selectedItem.x }}, {{ selectedItem.y }}

              </div>
            </div>
          </div>
        </q-card>
      </q-dialog>

    </div>
  </div>
</template>

<script>
import { onUpdated, ref, watch } from 'vue';

export default {
  props: {
    selectedItem: {
      type: Object,
      default: null
    },


  },
  setup(props) {
    const map = ref(null);
    const width = ref(820);

    const icon = ref(false);
    const pins = ref([]);
    const screenX = ref(0);
    const screenY = ref(0);
    const clientX = ref(0);
    const clientY = ref(0);
    let roomname = ref("");
    let roomdescription = ref("");

    // function addPin(event) {
    //   const mapElement = document.getElementById('map');
    //   const rect = mapElement.getBoundingClientRect();
    //   const x = event.clientX - rect.left;
    //   const y = event.clientY - rect.top;

    //   pins.value = [{ x, y }];
    // }

    function addPin2(x, y, name, description) {
      pins.value = [{ x, y }];
      roomname.value = name;
      roomdescription.value = description;
      console.log(roomname.value);
      console.log(roomdescription.value);
    }

    function logMousePosition(event) {
      screenX.value = event.screenX;
      screenY.value = event.screenY;
      clientX.value = event.clientX;
      clientY.value = event.clientY;
    }

    onUpdated(() => {
      width.value = map.value?.clientWidth ?? width.value;
      const rate = width.value / 820;
      pins.value = [{ x: pins.value[0].x * rate, y: pins.value[0].y * rate }];
    });

    watch(() => props.selectedItem, (newValue) => {
      icon.value = true;
      addPin2(newValue.x, newValue.y, newValue.name, newValue.description);
    })

    return {
      map,
      icon,
      pins,
      screenX,
      screenY,
      clientX,
      clientY,
      roomname,
      roomdescription,
      logMousePosition,
    };
  },
};
</script>

<style>
#map {
  position: relative;
  width: 100%;
  cursor: crosshair;
}

.map_image {
  width: 100%;
  object-fit: contain;
}

.pin {
  width: 30px;
  height: 30px;
  background-image: url("../assets/image/pin.png");
  background-size: cover;
  position: absolute;
  transform: translate(-48%, -90%);
}

.image-container {
  position: relative;
  display: inline-block;
}

.image-container img {
  display: block;
}

.log-container {
  padding: 8px;
  margin-top: 10px;

  bottom: 0;
  left: 0;
  width: 100%;
}

.my-dialog-content {
  width: fit-content;
  height: fit-content;

  border: 3px solid #000;
  -ms-overflow-style: none;
}

.pin-label {
  position: absolute;
  top: -50px;
  left: -50px;
  font-size: 12px;
  color: #000;
  background-color: #f3f0e8ed;
  padding: 2px 4px;
  width: 150px;
}

#img-card {
  -ms-overflow-style: none;
}
</style>
<template>
  <div>
    <div class="q-pa-md q-gutter-sm">
      

      <q-dialog v-model="icon">
        <q-card style="width: 800px; max-width: 100vw;">
          <div class="my-dialog-content">
            <div id="map" @mousemove="logMousePosition" @click="addPin" style="margin: 0 auto">
              <div v-for="(pin, index) in pins" :key="index" class="pin"
                :style="{ left: pin.x + 'px', top: pin.y + 'px' }">
                <span class="pin-label">{{ pin.x }}, {{ pin.y }}</span>
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
import { ref, watch } from 'vue';

export default {
  props: {
    selectedItem: {
      type: Object,
      default: null
    },


  },
  setup(props) {
    const icon = ref(false);
    const pins = ref([]);
    const screenX = ref(0);
    const screenY = ref(0);
    const clientX = ref(0);
    const clientY = ref(0);

    function addPin(event) {
      const mapElement = document.getElementById('map');
      const rect = mapElement.getBoundingClientRect();
      const x = event.clientX - rect.left;
      const y = event.clientY - rect.top;

      pins.value = [{ x, y }];
    }

    function addPin2(x, y) {
      pins.value = [{ x, y }];
    }

    function logMousePosition(event) {
      screenX.value = event.screenX;
      screenY.value = event.screenY;
      clientX.value = event.clientX;
      clientY.value = event.clientY;
    }

    watch(() => props.selectedItem, (newValue) => {
      icon.value = true;
      addPin2(newValue.x, newValue.y);
    })

    return {
      icon,
      pins,
      screenX,
      screenY,
      clientX,
      clientY,
      addPin,
      logMousePosition,
    };
  },
};
</script>

<style>
#map {
  position: relative;
  width: 800px;
  height: 600px;
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

  border: 1px solid #000;
}

.pin-label {
  position: absolute;
  top: -40px;
  /* ピンの上に表示する場合の調整 */
  left: 0;
  font-size: 12px;
  color: #000;
  background-color: #fff;
  padding: 2px 4px;
}
</style>
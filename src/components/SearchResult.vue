<template>
    <div class="q-ma-md" style="width: 720px; margin: 0 auto;">
        <q-scroll-area style="height: 100px;">
            <div v-for="n in 100" :key="n" id="div" class="q-py-xs" >
                <div class="contents">
                    <div style="width: 105px;">
                        <q-btn outline dense size="md" class="fa-14 q-px-sm" color="primary" style="width: 100px;">
                            <div class="text-black">教室</div>
                        </q-btn>
                    </div>
                    <div style="width: 300px;">
                        <q-btn outline dense size="md" class="fa-14 q-px-sm" color="primary" style="width: 300px;">
                            <div class="text-black">詳細</div>
                        </q-btn>
                    </div>
                </div>
            </div>
        </q-scroll-area>
    </div>


<!-- <div id="app">
    <div class="search">
      <v-text-field type="text" v-model="keyword" label="検索"></v-text-field>
    </div>
    <tr v-for="room in filteredRoom" :key="room.id">
      <td v-text="room.name"></td>
    </tr>
  </div>
-->
</template>


<style>
#div {
    display: flex;
    justify-content: center;
    background-color: rgba(105, 206, 155, 0.265);
}

.contents {
    text-align: left;
    height: 29px;
    display: flex;
    flex-direction: row;
}
</style>
<!--
<script>
  new Vue({
    data: {
      keyword: "",
      room: [
        {id: 1, name: "オレンジ"},
        {id: 2, name: "メロン" },
        {id: 3, name: "アップル"},
      ]
    },
    computed: {
      filteredRoom: function() {
        var room = [];
        for(var i in this.room) {
          var room_name = this.room[i];
          if(food.name.indexOf(this.keyword) !== -1) {
            room.push(food);
          }
        }
        return room;
      }
    }
  })
</script>
-->
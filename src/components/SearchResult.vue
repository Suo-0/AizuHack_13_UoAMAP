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
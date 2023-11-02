<template>
  <!-- <div class="q-ma-md" style="width: 720px; margin: 0 auto;">
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
    </div> -->




  <div class="q-pa-sm"
    style="background-color: #95e7ca8b; width: 720px; max-width: 100vw; margin: 0 auto; margin-top: 50px;">
    <q-scroll-area style="height: 500px;">
      <q-table style="background-color: #cedbf236;" :grid="$q.screen.xs" flat bordered :rows="rows" :columns="columns"
        row-key="name" :filter="filter" hide-header hide-pagination :pagination="pagination" :rows-per-page-options="[0]"
        @row-click="RowClick">
      </q-table>
    </q-scroll-area>
  </div>
</template>


<script>
import { ref, watch } from 'vue'

const columns = [
  {
    name: 'name',
    required: true,
    label: '名前',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  {
    name: 'description',
    label: '詳細',
    align: 'left',
    field: 'description',
    sortable: true
  },
  {
    name: 'number',
    label: '番号',
    align: 'center',
    field: 'number',
    sortable: true
  }
]

const rows = [
  {
    name: 'コンピュータ演習室(std1)',
    description: '研究棟1F',
    number: '143',
    x: 420,
    y: 390
  },
  {
    name: 'コンピュータ演習室(std2)',
    description: '研究棟1F',
    number: '146',
    x: 390,
    y: 390
  },
  {
    name: 'コンピュータ演習室(std3)',
    description: '講義棟1F',
    number: '101',
    x: 690,
    y: 520
  },
  {
    name: 'コンピュータ演習室(std4)',
    description: '講義棟1F',
    number: '102',
    x: 690,
    y: 450
  },
  {
    name: 'コンピュータ演習室(std5)',
    description: '研究棟1F',
    number: '103',
    x: 690,
    y: 390
  },
  {
    name: 'コンピュータ演習室(std6) ',
    description: '研究棟1F',
    number: '106',
    x: 660,
    y: 390
  },
  {
    name: '研究室・実験室',
    description: '研究棟1F',
    number: '101'
  },
  {
    name: '教員室',
    description: '研究棟1F',
    number: '102'
  },
  {
    name: '研究室・実験室',
    description: '研究棟1F',
    number: '104'
  },
  {
    name: '教員室',
    description: '研究棟1F',
    number: '105'
  },
  {
    name: 'シールド実験室',
    description: '研究棟1F',
    number: '107'
  },
  {
    name: '電磁波シールド室',
    description: '研究棟1F',
    number: '108'
  },
  {
    name: '音響驗室',
    description: '研究棟1F',
    number: '109'
  },
  {
    name: '無響室',
    description: '研究棟1F',
    number: '110'
  },
  {
    name: 'ネットワーク・遠隔講義室',
    description: '研究棟1F',
    number: '111'
  },
  {
    name: '研究室・実験室',
    description: '研究棟1F',
    number: '121'
  },
  {
    name: '教員室',
    description: '研究棟1F',
    number: '122'
  },
  {
    name: '企画運営室',
    description: '研究棟1F',
    number: '123'
  },
  {
    name: '研究棟事務連絡室',
    description: '研究棟1F',
    number: '124'
  },
  {
    name: '研究室・実験室',
    description: '研究棟1F',
    number: '125'
  },
  {
    name: '教員室',
    description: '研究棟1F',
    number: '126'
  },
  {
    name: '国際戦略本部・国際交流談話室',
    description: '研究棟1F',
    number: '127'
  },
  {
    name: '特別会議室',
    description: '研究棟1F',
    number: '128'
  },
  {
    name: 'ゼミ室(6)-(10)',
    description: '研究棟1F',
    number: '129~133'
  },
  {
    name: '工作室',
    description: '研究棟1F',
    number: '134'
  },
  {
    name: '印刷室',
    description: '研究棟1F',
    number: '135'
  },
  {
    name: '研究室・実験室',
    description: '研究棟1F',
    number: '141'
  },
  {
    name: '教員室',
    description: '研究棟1F',
    number: '142'
  },
  {
    name: '研究室・実験室',
    description: '研究棟1F',
    number: '144'
  },
  {
    name: '教員室',
    description: '研究棟1F',
    number: '145'
  },
  {
    name: '非常勤講師控室',
    description: '研究棟1F',
    number: '147'
  },
  {
    name: '保健室',
    description: '研究棟1F',
    number: '148'
  },
  {
    name: 'スタジオ',
    description: '研究棟1F',
    number: '149'
  },
  {
    name: 'Geek Dojo',
    description: '研究棟1F',
    number: '161',
    x: 570,
    y: 330
  },
  {
    name: 'SRLU2(ジム)',
    description: '研究棟1F',
    number: '162'
  },
  {
    name: '研究室・実験室',
    description: '研究棟2F',
    number: '201'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '202'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '203・204'
  },
  {
    name: '研究室・実験室',
    description: '研究棟2F',
    number: '205'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '206'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '207'
  },
  {
    name: 'システムサポートベースSSB',
    description: '研究棟2F',
    number: '207-E'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '207-F'
  },
  {
    name: '情報センター',
    description: '研究棟2F',
    number: '208'
  },
  {
    name: 'ハードウェア実験室（３）',
    description: '研究棟2F',
    number: '209'
  },
  {
    name: '情報センター図書ラウンジ',
    description: '研究棟2F',
    number: '210'
  },
  {
    name: '研究室',
    description: '研究棟2F',
    number: '211'
  },
  {
    name: '研究室・実験室',
    description: '研究棟2F',
    number: '221'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '222'
  },
  {
    name: '研究室',
    description: '研究棟2F',
    number: '223'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '224'
  },
  {
    name: '研究室・実験室',
    description: '研究棟2F',
    number: '225'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '226'
  },
  {
    name: 'ハードウェア実験室（４）',
    description: '研究棟2F',
    number: '227'
  },
  {
    name: '研究室・実験室',
    description: '研究棟2F',
    number: '241'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '242'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '243'
  },
  {
    name: '客員教員室',
    description: '研究棟2F',
    number: '243-B'
  },
  {
    name: '文化研究センター',
    description: '研究棟2F',
    number: '244・248'
  },
  {
    name: '実験室',
    description: '研究棟2F',
    number: '245'
  },
  {
    name: '修学支援室',
    description: '研究棟2F',
    number: '246-E',
    x: 390,
    y: 520
  },
  {
    name: '実験室',
    description: '研究棟2F',
    number: '246-F'
  },
  {
    name: '教員室',
    description: '研究棟2F',
    number: '247'
  },
  {
    name: '学生相談室',
    description: '研究棟2F',
    number: '252'
  },
  {
    name: '語学研究室',
    description: '研究棟2F',
    number: '253'
  },
  {
    name: 'CLR-eﾗｰﾆﾝｸﾞ･ﾕｰｻﾞﾋﾞﾘﾃｨﾗﾎﾞ',
    description: '研究棟2F',
    number: '261'
  },
  {
    name: '語学研究室',
    description: '研究棟2F',
    number: '262～266・269～274'
  },
  {
    name: 'CLR-技術的ｺﾐｭﾆｹｰｼｮﾝﾗﾎﾞ',
    description: '研究棟2F',
    number: '267'
  },
  {
    name: 'CLR-音声学ラボ',
    description: '研究棟2F',
    number: '268'
  },
  {
    name: '小講義室Ｓ１－Ｓ４',
    description: '研究棟2F',
    number: '275'
  },
  {
    name: 'CALL1',
    description: '研究棟2F',
    number: '276'
  },
  {
    name: 'iLab1',
    description: '研究棟2F',
    number: '277',
    x: 560,
    y: 330
  },
  {
    name: '語学研究センター事務室',
    description: '研究棟2F',
    number: '278'
  },
  {
    name: 'iLab2',
    description: '研究棟2F',
    number: '279',
    x: 525,
    y: 335
  },
  {
    name: 'CALL2',
    description: '研究棟2F',
    number: '280'
  },
  {
    name: '小講義室Ｓ５－Ｓ８',
    description: '研究棟2F',
    number: '281'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '301'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '302'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '303'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '304'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '305'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '306'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '307'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '308'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '321'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '322'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '323'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '324'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '325'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '326'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '327'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '328'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '341'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '342'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '343'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '344'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '345'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '346'
  },
  {
    name: '教員室',
    description: '研究棟3F',
    number: '347'
  },
  {
    name: '研究室・実験室',
    description: '研究棟3F',
    number: '348'
  },
  {
    name: '中講義室M11',
    description: '研究棟3F',
    number: '361',
    x: 600,
    y: 570
  },
  {
    name: '中講義室M12',
    description: '研究棟3F',
    number: '362',
    x: 630,
    y: 570
  },
  {
    name: '研究室・実験室・小講義室(S9,S10)',
    description: '研究棟3F',
    number: '363'
  },
  {
    name: '小講義室(S11,S12)',
    description: '研究棟3F',
    number: '364'
  },
  {
    name: '中講義室M8',
    description: '講義棟1F',
    number: '103'
  },
  {
    name: '中講義室M9',
    description: '講義棟1F',
    number: '104'
  },
  {
    name: '中講義室M10',
    description: '講義棟1F',
    number: '105'
  },
  {
    name: '中講義室M1',
    description: '講義棟2F',
    number: '201'
  },
  {
    name: '中講義室M2',
    description: '講義棟2F',
    number: '202'
  },
  {
    name: '中講義室M3',
    description: '講義棟2F',
    number: '203'
  },
  {
    name: '中講義室M4',
    description: '講義棟2F',
    number: '204'
  },
  {
    name: '中講義室M5',
    description: '講義棟2F',
    number: '205'
  },
  {
    name: '中講義室M6',
    description: '講義棟2F',
    number: '206'
  },
  {
    name: '中講義室M7',
    description: '講義棟2F',
    number: '207'
  },
  {
    name: 'ハードウェア実験室（１）',
    description: '講義棟2F',
    number: '208'
  },
  {
    name: 'ハードウェア準備室',
    description: '講義棟2F',
    number: '209'
  },
  {
    name: 'ハードウェア実験室（２）',
    description: '講義棟2F',
    number: '210'
  },
  {
    name: '講堂',
    description: '講堂',
    number: 'Aud'
  },
  {
    name: '控室(1)',
    description: '講堂',
    number: 'WR1'
  },
  {
    name: '控室(2)',
    description: '講堂',
    number: 'WR2'
  }
]

export default {
  props: {
    filter: {
      type: String,
      required: true
    }
  },

  setup(props) {
    return {
      columns,
      rows
    };
  },

  methods: {
    RowClick(row, index) {
      this.$emit('itemClick', { x: index.x, y: index.y, name: index.name, description: index.description });
    }
  }
}
</script>

<!-- <style>
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
</style> -->
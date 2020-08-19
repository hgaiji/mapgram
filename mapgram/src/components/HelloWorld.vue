<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Welcome to Mapgram
        </h1>

        <p class="subheading font-weight-regular">
          For help and collaboration with other Vuetify developers,
          <br>please join our online
          <a
            href="https://community.vuetifyjs.com"
            target="_blank"
          >Discord Community</a>
        </p>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        <h2 class="headline font-weight-bold mb-3">
          What's next?
        </h2>

        <v-row justify="center">
          <div id="regions_div">
          </div>
      <MapDialog ref="MapDialog"/>

        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>
<script src="https://www.gstatic.com/charts/loader.js"></script>
<script>
import MapDialog from './MapDialog';
  export default {
    name: 'HelloWorld',
    components: {
      MapDialog
    },

    data: () => ({
    }),
    mounted: function () {
      const self = this;
    google.charts.load('current', {
        'packages':['geochart'],
        // Note: you will need to get a mapsApiKey for your project.
        // See: https://developers.google.com/chart/interactive/docs/basic_load_libs#load-settings
        'mapsApiKey': 'AIzaSyD-9tSrke72PouQMnMX-a7eZSW0jkFMBWY'
      });
      google.charts.setOnLoadCallback(drawRegionsMap);
      function drawRegionsMap() {
        var data = google.visualization.arrayToDataTable([
          ['都道府県', '写真'],
          ['北海道', 0],
          ['青森', 0],
          ['秋田', 0],
          ['岩手', 0],
          ['宮城', 0],
          ['山形', 0],
          ['福島', 0],
          ['栃木', 0],
          ['群馬', 0],
          ['茨城', 0],
          ['東京', 0],
          ['埼玉', 0],
          ['千葉', 0],
          ['神奈川', 0],
          ['静岡', 0],
          ['愛知', 0],
          ['岐阜', 0],
          ['三重', 0],
          ['滋賀', 0],
          ['京都', 0],
          ['大阪', 0],
          ['奈良', 0],
          ['和歌山', 0],
          ['兵庫', 0],
          ['徳島', 0],
          ['香川', 0],
          ['愛媛', 0],
          ['高知', 0],
          ['福岡', 0],
          ['佐賀', 0],
          ['長崎', 0],
          ['大分', 0],
          ['熊本', 0],
          ['宮崎', 0],
          ['鹿児島',0],
          ['沖縄', 0],
          ['岡山', 0],
          ['広島', 0],
          ['山口', 0],
          ['鳥取', 0],
          ['島根', 0],
          ['石川', 0],
          ['福井', 0],
          ['富山', 0],
          ['山梨', 0],
          ['長野', 0],
          ['新潟', 0]
        ]);
        var options = {
          region: 'JP',
          resolution: 'provinces'
        };
        var chart = new google.visualization.GeoChart(document.getElementById('regions_div'));
        chart.draw(data, options);
        google.visualization.events.addListener(chart, 'regionClick', selectHandler);
        
        function selectHandler(reg) {
          console.log(reg);
          let comp = self.$refs.MapDialog
          console.log(self.$refs);
          comp.openDialog(self.convertIso3166(reg.region))
        }
      };
  },
  methods: {
    convertIso3166: function(reg){
      const region = {
        "JP-01":"北海道"	,
        "JP-02":"青森県"	,
        "JP-03":"岩手県"	,
        "JP-04":"宮城県"	,
        "JP-05":"秋田県"	,
        "JP-06":"山形県"	,
        "JP-07":"福島県"	,
        "JP-08":"茨城県"	,
        "JP-09":"栃木県"	,
        "JP-10":"群馬県"	,
        "JP-11":"埼玉県"	,
        "JP-12":"千葉県"	,
        "JP-13":"東京都"	,
        "JP-14":"神奈川県",
        "JP-15":"新潟県"	,
        "JP-16":"富山県"	,
        "JP-17":"石川県"	,
        "JP-18":"福井県"	,
        "JP-19":"山梨県"	,
        "JP-20":"長野県"	,
        "JP-21":"岐阜県"	,
        "JP-22":"静岡県"	,
        "JP-23":"愛知県"	,
        "JP-24":"三重県"	,
        "JP-25":"滋賀県"	,
        "JP-26":"京都府"	,
        "JP-27":"大阪府"	,
        "JP-28":"兵庫県"	,
        "JP-29":"奈良県"	,
        "JP-30":"和歌山県",
        "JP-31":"鳥取県"	,
        "JP-32":"島根県"	,
        "JP-33":"岡山県"	,
        "JP-34":"広島県"	,
        "JP-35":"山口県"	,
        "JP-36":"徳島県"	,
        "JP-37":"香川県"	,
        "JP-38":"愛媛県"	,
        "JP-39":"高知県"	,
        "JP-40":"福岡県"	,
        "JP-41":"佐賀県"	,
        "JP-42":"長崎県"  ,
        "JP-43":"熊本県"	,
        "JP-44":"大分県"	,
        "JP-45":"宮崎県"	,
        "JP-46":"鹿児島県",
        "JP-47":"沖縄県"	,
      };
      return region[reg];
    }
  }
  }
</script>

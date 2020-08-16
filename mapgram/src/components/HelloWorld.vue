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
          Welcome to Vuetify
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
      ecosystem: [
        {
          text: 'vuetify-loader',
          href: 'https://github.com/vuetifyjs/vuetify-loader',
        },
        {
          text: 'github',
          href: 'https://github.com/vuetifyjs/vuetify',
        },
        {
          text: 'awesome-vuetify',
          href: 'https://github.com/vuetifyjs/awesome-vuetify',
        },
      ],
      importantLinks: [
        {
          text: 'Documentation',
          href: 'https://vuetifyjs.com',
        },
        {
          text: 'Chat',
          href: 'https://community.vuetifyjs.com',
        },
        {
          text: 'Made with Vuetify',
          href: 'https://madewithvuejs.com/vuetify',
        },
        {
          text: 'Twitter',
          href: 'https://twitter.com/vuetifyjs',
        },
        {
          text: 'Articles',
          href: 'https://medium.com/vuetify',
        },
      ],
      whatsNext: [
        {
          text: 'Explore components',
          href: 'https://vuetifyjs.com/components/api-explorer',
        },
        {
          text: 'Select a layout',
          href: 'https://vuetifyjs.com/getting-started/pre-made-layouts',
        },
        {
          text: 'Frequently Asked Questions',
          href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
        },
      ],
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
          comp.openDialog()
        }
      };
  }
  }
</script>

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="regions_div">
    </div>
  </div>
</template>
<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted: function () {
    google.charts.load('current', {
        'packages':['geochart'],
        // Note: you will need to get a mapsApiKey for your project.
        // See: https://developers.google.com/chart/interactive/docs/basic_load_libs#load-settings
        'mapsApiKey': ''
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
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

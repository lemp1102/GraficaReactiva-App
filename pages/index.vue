<template>
  <v-row justify='center' align='center'>
    <v-col sm='8' md='6'>
      <v-select
        v-model='periodo'
        :items="items"
        label="Período"
        outlined
        @input='dataSetChage'>
      </v-select>
      <BarChart :chart-data='chartData' :options='barChartOptions' />
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      items: ["Primer Semestre", "Segundo Semestre"],
      barChartData: [
        {
          labels: [
            "Enero",
            "Febrero",
            "Marzo",
            "Abril",
            "Mayo",
            "Junio",
          ],
          datasets: [
            {
              label: "Visualizaciones",
              data: [2, 1, 16, 3, 4, 5],
              backgroundColor: "rgba(20, 255, 0, 0.3)",
              borderColor: "rgba(100, 255, 0, 1)",
              borderWidth: 2,
            },
          ],
        },
        {
          labels: [
            "Julio",
            "Agosto",
            "Septiembre",
            "Octubre",
            "Noviembre",
            "Diciembre",
          ],
          datasets: [
            {
              label: "Visualizaciones",
              data: [0, 0, 4, 12, 2, 15],
              backgroundColor: "rgba(20, 255, 0, 0.3)",
              borderColor: "rgba(100, 255, 0, 1)",
              borderWidth: 2,
            },
          ],
        },
      ],
      barChartOptions: {
        responsive: true,
        legend: {
          display: false,
        },
        title: {
          display: true,
          text: "Google analytics data",
          fontSize: 24,
          fontColor: "#6b7280",
        },
        tooltips: {
          backgroundColor: "#17BF62",
        },
        scales: {
          xAxes: [
            {
              gridLines: {
                display: true,
              },
            },
          ],
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
                max: 7,
                min: 0,
                stepSize: 1,
              },
              gridLines: {
                display: true,
              },
            },
          ],
        },
      },
      chartData: '',
      periodo: ''
    };
  },
  mounted() {
    this.chartData= this.barChartData[0];
  },
  methods: {
    dataSetChage(){
      switch (this.periodo) {
        case "Primer Semestre":   this.chartData =
          {
            labels: [
              "Enero",
              "Febrero",
              "Marzo",
              "Abril",
              "Mayo",
              "Junio",
            ],
            datasets: [
              {
                label: "Visualizaciones",
                data: [2, 1, 16, 3, 4, 5],
                backgroundColor: "rgba(20, 255, 0, 0.3)",
                borderColor: "rgba(100, 255, 0, 1)",
                borderWidth: 2,
              },
            ],
          };
                                  console.log(this.chartData);
                                  break;
        case "Segundo Semestre":  this.chartData = {
          labels: [
            "Julio",
            "Agosto",
            "Septiembre",
            "Octubre",
            "Noviembre",
            "Diciembre",
          ],
          datasets: [
            {
              label: "Visualizaciones",
              data: [0, 0, 4, 12, 2, 15],
              backgroundColor: "rgba(20, 255, 0, 0.3)",
              borderColor: "rgba(100, 255, 0, 1)",
              borderWidth: 2,
            },
          ],
        };
                                  console.log(this.chartData);
                                  break;
      }
    }
  },

};
</script>

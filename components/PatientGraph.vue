<template>
  <div class="patient-graph">
    <client-only>
      <Apexcharts type="line" :options="chartOptions" :series="series" />
    </client-only>
  </div>
</template>

<script>
export default {
  name: 'PatientGraph',
  data() {
    return {
      chartOptions: {
        chart: {
          type: 'line',
          zoom: {
            enabled: false,
          },
        },
        legend: {
          position: 'top',
          horizontalAlign: 'left',
          inverseOrder: true,
        },
        colors: ['#4CD964', '#E24242', '#855CF8'],
        stroke: {
          curve: 'straight',
          width: 2,
        },
        labels: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16],
        yaxis: [
          {
            seriesName: '体温',
            decimalsInFloat: 1,
            labels: {
              style: {
                colors: ['#4CD964'],
              },
            },
            min: 34,
            max: 40,
            crosshairs: {
              show: true,
              position: 'back',
            },
            tooltip: {
              enabled: true,
            },
            float: true,
          },
          {
            seriesName: '血圧',
            decimalsInFloat: 0,
            labels: {
              style: {
                colors: ['#E24242'],
              },
            },
            min: 30,
            max: 150,
            crosshairs: {
              show: true,
              position: 'back',
            },
            tooltip: {
              enabled: true,
            },
            float: true,
          },
          {
            seriesName: 'SpO2',
            decimalsInFloat: 0,
            labels: {
              style: {
                colors: ['#855CF8'],
              },
            },
            min: 90,
            max: 100,
            crosshairs: {
              show: true,
              position: 'back',
            },
            tooltip: {
              enabled: true,
            },
            float: true,
          },
        ],
      },
      series: [
        {
          name: '体温',
          data: [
            35.4,
            35.0,
            36.0,
            36.4,
            36.6,
            36.9,
            37.5,
            36.4,
            36.5,
            36.3,
            37.2,
            37.5,
            38.5,
            37.5,
            36.5,
          ],
        },
        {
          name: '血圧',
          data: [
            120,
            132,
            121,
            104,
            99,
            96,
            84,
            90,
            100,
            104,
            105,
            104,
            123,
            110,
            130,
          ],
        },
        {
          name: 'SpO2',
          data: [99, 98, 96, 97, 96, 97, 98, 99, 100, 100, 97, 98, 99, 96, 95],
        },
      ],
    }
  },
}
</script>

<style lang="scss">
.patient-graph {
  height: 100%;
  width: 100%;
  &__y-axis {
    &__title {
      &__body-tempreture {
        width: 0;
        &::before {
          content: '体温' !important;
          width: 100% !important;
        }
      }
    }
  }
}
</style>

<script>
  import Highcharts from "highcharts";
  import Chart from "@highcharts/svelte";

  let options = {
    chart: {
      type: "column",
      height: 500,
    },
    title: {
      text: "Health Insurance Coverage for Black Texans (by Quartile, 2023)",
    },
    xAxis: {
      categories: [
        "Bottom 25%",
        "26–50%",
        "51–75%",
        "Top 25%",
      ],
      title: {
        text: "Coverage Quartile",
      },
    },
    yAxis: {
      min: 0,
      title: {
        text: "Number of Counties",
      },
    },
    tooltip: {
      shared: true,
      valueSuffix: " counties",
    },
    plotOptions: {
      column: {
        colorByPoint: true,
        colors: ['#ff4d4f', '#ffa940', '#ffd666', '#73d13d'],
        dataLabels: {
          enabled: true,
          format: '{y}',
        }
      }
    },
    series: [
      {
        name: "Counties",
        data: [104, 60, 23, 44],
      },
    ],
    credits: {
      enabled: false,
    },
  };
</script>

<div class="chart">
  <Chart {options} highcharts={Highcharts} />
</div>

<style>
  .chart {
    width: 100%;
    margin: 2rem auto;
  }
</style>

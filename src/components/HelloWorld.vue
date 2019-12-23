<template>
  <div class='display'>
    <h1>Forex charts</h1>
    <div class='charts-container'>
      <div class="chart">
       <TestChart :series = "eurusd" pair="EUR/USD"/>
      </div>
      <div class="chart">
        <TestChart :series = "gbpusd" pair="GBP/USD"/>
      </div>
      <div class="chart">
         <TestChart :series = "audusd" pair="GBP/USD"/>
      </div>

      <h1>Realtime values: </h1>
      <div class='fores-values'>
        <div class='row'>
          <div class='col'>EUR/USD: </div>
          <div class='col'>{{lastEURUSD}}</div>
        </div>
        <div class='row'>
          <div class='col'>GBP/USD: </div>
          <div class='col'>{{lastGPBUSD}}</div>
        </div>
        <div class='row'>
          <div class='col'>AUS/USD: </div>
          <div class='col'>{{lastAUSUSD}}</div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>

import TestChart from './TestChart';

export default {
  name: 'HelloWorld',
  components: {
    TestChart
  },
  props: {
    msg: String,
    pair: String
  },
  data:function() { 
    return {
    lastEURUSD:1.1,
    lastGPBUSD:1.2,
    lastAUSUSD:1.3
    }
  },

  created: function() {

    setInterval(()=> {
      this.lastEURUSD = Math.floor(Math.random() * 100)/100;
      this.lastGPBUSD = Math.floor(Math.random() * 100)/100;
      this.lastAUSUSD = Math.floor(Math.random() * 100)/100;  

    this.eurusd[0].data.push(this.lastEURUSD);
    this.gbpusd[0].data.push(this.lastGPBUSD);
    this.audusd[0].data.push(this.lastAUSUSD)

    }, 1000);
  

  },
  computed: {
  eurusd : function() {
      return [{
              name: 'EUR/USD',
              data: [1.11, 1.2, 1.5, 1.6, 1.5, 2, 1.7, 1.65, 1.23, 1.33, 1.23, 1.1]
          }];
    },
  gbpusd: function() {
    return [{
              name: 'GBP/USD',
              data: [1.11, 1.2, 1.5, 1.6, 1.5, 2, 1.7, 1.65, 1.23, 1.33, 1.23, 1.1]
          }];
    },
    audusd: function() {
      return [{
              name: 'AUD/USD',
              data: [1.11, 1.2, 1.5, 1.6, 1.5, 2, 1.7, 1.65, 1.23, 1.33, 1.23, 1.1]
      }];
    }
    }
}
</script>

<style scoped>

  h1 {
    padding: 20px;
  }

  .display {
    width: 1200px;
    margin: 0 auto;
  }
  .chart {
    width: 100%;
    height: 500px;
    margin: 20px;
    border-radius: 3px;
    color: white;
  }

.fores-values {
  width: 300px;
}

.fores-values .row {
  display: flex;
}

.fores-values .row .col{
  width: 50%;
  margin: 5px;
  text-align: center;
  border: 2px solid black;
}

</style>

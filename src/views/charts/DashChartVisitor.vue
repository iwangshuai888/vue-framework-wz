<template>

  <Col :span="24">
    <chart :options="option" class="echarts" id="chart" > </chart>

  </Col>

</template>

<style scoped>
.echarts {
  border-radius:4px;
    
  height: 250px;
  width: 100%;

}


</style>

<script>



var data = [{
    value: 3661,
    name: '>0'
}, {
    value: 5713,
    name: '0-100'
}, {
    value: 9938,
    name: '100-500'
}, {
    value: 17623,
    name: '500-2000'
}, {
    value: 3299,
    name: '>2000'
}];


export default {
    mounted(){
    },
  data: function () {
   
    return {





option : {
    backgroundColor: '#49586e',
    title: {
        text: '积分分布图',
        x: '24%',
        y: 'center',
        textStyle: {
            fontWeight: 'normal',
            fontSize: 20,
             color: '#fff',
        }
    },
    tooltip: {
        show: true,
        trigger: 'item',
        formatter: "{b}: {c} ({d}%)"
    },
    legend: {
        orient: 'vertical',
        right: '5%',
         top: '25%',
           textStyle: {
            fontWeight: 'normal',
            fontSize: 16,
             color: '#fff',
        },
        data: ['>0', '0-100', '100-500', '500-2000', '>2000']
    },
    series: [{
        type: 'pie',
        selectedMode: 'single',
         center: ['30%', '50%'],
        radius: ['50%', '80%'],
        // color: ['#86D560', '#AF89D6', '#59ADF3', '#FF999A', '#FFCC67'],
        color: ['#AF89D6', '#5ab6df', '#6a8bc0', '#4acacb', '#fe8676'],

        label: {
            normal: {
                position: 'inner',
                formatter: '{d}%',

                textStyle: {
                    color: '#fff',
                    fontWeight: 'bold',
                    fontSize: 12
                }
            }
        },
        labelLine: {
            normal: {
                show: false
            }
        },
        data: data
    }]
}
  
    



    }
  }
}
</script>
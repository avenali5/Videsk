<template>
    <div class="chart">
        <Plotly :data="data" :layout="layout" :display-mode-bar="false" class="pie"></Plotly>
    </div>
</template>

<script>
import { Plotly } from 'vue-plotly'

export default {
  components: {
    Plotly
  },
  data(){
    return{
        data:{
            data:[{
                labels: [],
                values: [],
                type:"pie",
            }],
            layout:{
                colorway:[
                    '#E289F2',
                    '#ACB9FF',
                    '#855CF8',
                    '#200C57'
                ],
            }
        },
    }
  },
  async mounted(){
        const reportResponse = await fetch('/api/reports');
        const reports = await reportResponse.json();
        let reasons = reports.reports

        reasons.forEach(reason => {
            this.data.data[0].labels.push(reason.category)
            this.data.data[0].values.push(reason.total)
        })
  }
}

</script>

<style scoped lang="scss">
</style>
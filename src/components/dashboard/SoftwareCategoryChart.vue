<template>
<div>
    <p id="chart-title"><center><b>Software Category Classification</b></center></p>
    <ejs-treemap id='chart004' :leafItemSettings='leafItemSettings'
     format='n' :useGroupingSeparator='useGroupingSeparator'
    :dataSource='dataSource' :legendSettings='legendSettings' :palette='palette' :tooltipSettings='tooltipSettings'
    :weightValuePath='weightValuePath' :levels='levels'>
    </ejs-treemap>
</div>
</template>
<script>
import Vue from 'vue'
import { TreeMapPlugin, TreeMapTooltip, TreeMapLegend } from '@syncfusion/ej2-vue-treemap'

Vue.use(TreeMapPlugin)
export default Vue.extend({
  data: function () {
    return {
        useGroupingSeparator: true,
        dataSource: this.$store.state.softwareInput,
        legendSettings: {
            visible: true,
            position: 'Bottom',
            shape: 'Rectangle',
            shapeHeight: 7,
            shapeWidth: 7
        },
        palette: ['rgb(13, 202, 85)', '#D075C6', '#7E7EDC', '#7EC9DC', 'rgb(202, 158, 13)'],
        tooltipSettings: {
            visible: true,
            // eslint-disable-next-line
            format: '${Name}<br>License Count : ${LicenseCount}'
        },
        leafItemSettings: {
            labelPath: 'Name',
            border: { color: '#000000', width: 0.5 }
        },
        weightValuePath: 'LicenseCount',
        levels: [
            {
                groupPath: 'Category', border: 'none' // { color: 'white', width: 1 }
            }
        ]
    }
  },
  provide: {
    treemap: [TreeMapTooltip, TreeMapLegend]
  }
})
</script>
<style scoped>

</style>

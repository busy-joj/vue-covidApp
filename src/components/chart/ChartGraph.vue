<template>
    <canvas width="400" height="400" ref="myChart"></canvas>
</template>

<script>
import { Chart, registerables } from "chart.js"
Chart.register(...registerables);

export default {
    name:'ChartGraph',
    props:{
        chartOptions:{
            type : Object,
            default(){
                return{
                    type:"bar",
                    labels:["red","blus"],
                    datasets:[
                        {
                            data:[12,19],
                            label:"test",
                            borderWidth:1,                       
                            backgroundColor: [
                                'rgba(255, 99, 132, 0.2)',
                                'rgba(54, 162, 235, 0.2)'
                            ],
                            borderColor: [
                                'rgba(255, 99, 132, 1)',
                                'rgba(54, 162, 235, 1)',
                                'rgba(255, 206, 86, 1)',
                                'rgba(75, 192, 192, 1)',
                                'rgba(153, 102, 255, 1)',
                                'rgba(255, 159, 64, 1)'
                            ],
                            options: {
                                scales: {
                                    y: {
                                        beginAtZero: true
                                    }
                                }
                            }
                        }
                    ]
                }
            }
        }
    },
    data(){
        return{
            chartObject:null
        }
    },
    mounted(){
        this.drawChart()
    },
    methods:{
        drawChart(){
            const { type, datasets, labels, options } = this.chartOptions
            const ctx = this.$refs.myChart.getContext('2d');
            this.chartObject = new Chart(ctx, {
                type: type,
                data: {
                    labels,
                    datasets
                },
                options
            });
        }   
    }    
}
</script>

<style>

</style>
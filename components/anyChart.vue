<template>
    <div>
        {{ title }}
        <canvas :id="id"></canvas>
    </div>
</template>
<script>
    import Chart from 'chart.js'
    export default {
        props: [ 'id', 'title', 'type', 'labels', 'datasets', 'options' ],
        mounted () {
            console.log(this.labels)
            var ctx = document.getElementById(this.id).getContext('2d');
            var myChart = new Chart(ctx, {
                type: this.type,
                data: {
                    labels: this.labels,
                    datasets: this.datasets
                },
                options: this.options
            })
        }
    }
</script>
<template>
    <div class="container text-center p-4">
        <h1 class="fw-bold text-uppercase fs-1">{{text}}</h1>
        <div>{{timestamp}}</div>
    </div>
</template>

<script>
import moment from 'moment'

export default{
    name: 'DataTitle',
    props: ['text', 'dataDate'],
    computed: {
        timestamp: function(){
            return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
        }
    }
}
</script>
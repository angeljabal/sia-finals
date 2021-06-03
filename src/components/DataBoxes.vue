<template>

<div class="col-md-6 offset-md-3">
        <div class="row row-cols-1 row-cols-md-3 g-4">
            <div class="col">
                <div class="card">
                <div class="card-body">
                    <p class="card-title fw-bold text-secondary">Cases</p>
                    <div class="mb-2">
                        <h3>
                        {{ numberWithCommas(stats.TotalConfirmed) }}
                        </h3>
                        <p style="font-size: 15px; color: #62757f">{{timestamp}}</p>    
                        <p class="fst-italic">Number of active cases of COVID-19</p>
                    </div>
                </div>
                </div>
                <div class="card-footer bg-info"></div>
            </div>
            <div class="col">
                <div class="card">
                <div class="card-body">
                    <p class="card-title fw-bold text-secondary">Recovered</p>
                    <div class="mb-2">
                        <h3>
                        {{ numberWithCommas(stats.TotalRecovered) }}
                        </h3>
                        <p style="font-size: 15px; color: #62757f">{{timestamp}}</p>
                        <p class="fst-italic">Number of recoveries from COVID-19</p>
                    </div>
                </div>
                </div>
                <div class="card-footer bg-success"></div>
            </div>
            <div class="col">
                <div class="card">
                <div class="card-body">
                    <p class="card-title fw-bold text-secondary">Deaths</p>
                    <div class="mb-2">
                        <h3>
                        {{ numberWithCommas(stats.TotalDeaths) }}
                        </h3>
                        <p style="font-size: 15px; color: #62757f">{{timestamp}}</p>
                        <p class="fst-italic">Number of deaths caused by COVID-19</p>
                    </div>
                </div>
                </div>
                <div class="card-footer bg-danger"></div>
            </div>
        </div>

    </div>
    
</template>

<script>
import moment from 'moment'

export default {
    name: 'DataBoxes',
    props: ['stats'],
    computed: {
        timestamp: function(){
            return moment(this.dataDate).format('ddd MMMM DD, YYYY')
        }
    },
    methods: {
        numberWithCommas(x){
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
}
</script>
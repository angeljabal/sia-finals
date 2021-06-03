<template>
    <div class="col-md-6 offset-md-3 p-4" style="margin-top: 30px">
    <select @change="onChange()"
        v-model="selected" class="form-select">
            <option value="0">Select Country</option>
            <option v-for="country in countries" :value="country.ID">
                {{ country.Country }}
            </option>
        </select>
    </div>   
</template>

<script>
export default {
    name: 'CountrySelect',
    props: ['countries'],
    data(){
        return {
            selected: 0
        }
    },
    methods: {
        onChange(){
            const country = this.countries.find((item) => item.ID === this.selected)
            this.$emit('get-country', country)
        }
    }
}
</script>
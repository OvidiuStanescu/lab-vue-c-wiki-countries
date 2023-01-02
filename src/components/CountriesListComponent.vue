<template>
<div class="col-5" style="max-height: 90vh; overflow: scroll">
    <div v-if="data" v-for="country in data" :key="country.alpha3Code" class="list-group">
            <router-link v-bind:style="{textDecoration: 'none'}" :to="`/list/${country.alpha3Code}`">
                <div @country-selected="countryHandler" class="list-group-item list-group-item-action">
                    <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`" alt="country flag">
                    <p>{{ country.name.official }}</p>
                </div>
            </router-link>
    </div>
</div>
<CountryDetailsComponent :country="selectedCountry"></CountryDetailsComponent> 
</template>

<script>
import CountryDetailsComponent from "./CountryDetailsComponent.vue"
export default{
    components:{
        CountryDetailsComponent
    },
    created(){
        let id = this.$route.params.alpha3Code
        if(id) this.selectedCountry = this.data.find(el => el.alpha3Code === id)
    },
    data() {
        return{
            selectedCountry: null
        }
    },
    props:{
        data: {
            type: Array,
            default: {}
        }
    },
    methods:{
        countryHandler(data){
            this.selectedCountry = data
        }
    },
    watch: {
        "$route.params.alpha3Code"(){
            if(this.data){
                this.selectedCountry = this.data.find(el => el.alpha3Code === this.$route.params.alpha3Code)
            }
        }
    }
}
</script>

<style>
</style>
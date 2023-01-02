<template>
<div v-if="country" class="col-7">
            <img v-if="country" :src="`https://flagpedia.net/data/flags/w580/${country.alpha2Code.toLowerCase()}.webp`" alt="country flag" style="width: 300px"/>
            <h1>{{ country.name.official }}</h1>
            <table class="table">
              <thead></thead>
              <tbody>
                <tr>
                  <td style="width: 30%">Capital</td>
                  <td>{{ country.capital[0] }}</td>
                </tr>
                <tr>
                  <td>Area</td>
                  <td>
                    <sup>{{ country.area }}</sup>
                  </td>
                </tr>
                <tr>
                  <td>Borders</td>
                  <td>
                    <ul v-if="borders.length>0" v-for="border in borders">
                      <li><a href="#">{{ border }}</a></li>
                    </ul>  
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
</template>

<script>
export default{
    data() {
        return{
            borders: this.country.borders
        }
    },
    props:{
        country: {
            type: Object,
            default: {}
        }
    }
}
</script>

<style>
</style>
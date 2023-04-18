<template>
    <div class="container">
        <div class="row">
            <div class="col-5" style="max-height: 90vh; overflow: scroll">
                <div class="list-group">
                    <router-link v-for="country in countries" :key="country.alpha3Code"
                        class="list-group-item list-group-item-action"
                        :to="{ name: 'details', params: { alpha3Code: country.alpha3Code } }">
                        <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code}.png`" alt="country flag">
                        <p>{{ country.name }}</p>
                    </router-link>
                </div>
            </div>
            <router-view :countries="countries" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            countries: []
        }
    },

    created() {
        fetch('https://ih-countries-api.herokuapp.com/countries')
            .then(response => response.json())
            .then(data => {
                this.countries = data.map(elem => ({
                    alpha2Code: elem.alpha2Code.toLowerCase(),
                    alpha3Code: elem.alpha3Code,
                    name: elem.name.common,
                    borders: elem.borders,
                    capital: elem.capital[0],
                    area: elem.area
                }))
            })
    },
}
</script>
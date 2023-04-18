<template>
    <div class="col-7">
        <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code}.png`" alt="country flag">
        <h1>{{ country.name }}</h1>
        <table class="table">
            <thead>
            </thead>
            <tbody>
                <tr>
                    <td style="width: 30%">Capital: {{ country.capital }}</td>
                    <td>{{ country.name }}</td>
                </tr>
                <tr>
                    <td>Area</td>
                    <td>{{ country.area }} km <sup>2</sup></td>
                </tr>
                <tr>
                    <td>Borders</td>
                    <td>
                        <ul>
                            <li v-for="border in country.borders" :key="border">
                                <router-link :to="{ name: 'details', params: { alpha3Code: border } }">
                                    {{ border }}
                                </router-link>
                            </li>
                        </ul>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

export default {
    props: {
        countries: {
            type: Array
        },
    },

    data() {
        return {
            alpha3Code: this.$route.params.alpha3Code,
            country: null,
        }
    },

    mounted() {
        console.log(this.countries)
    },

    computed: {
        country() {
            if (this.countries.length === 0) {
                return {}
            }
            return this.countries.find(c => c.alpha3Code === this.$route.params.alpha3Code) || {}
        }
    },

    watch: {
        alpha3Code(newValue, oldValue) {
            console.log(newValue)
            console.log(oldValue)
            return this.country = this.countries.find(country => country.alpha3Code === newValue)
        }

    }
}

</script>

<template>
    <div class="container">
      <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">

        <!-- a single row from an array  -->
        <div class="col"  v-for="country in countries" :key="country">
          <div class="card shadow-sm">
            <img class="card-img-top" :src="country.flag" alt="Card image cap">
            <div class="card-body">
              <strong class="card-text">{{ country.name }}</strong>
              <p>
                Capital: {{ country.capital }} 
                <!-- CallingCodes: {{ country.callingCodes }} <br>
                Alpha2Code: {{ country.alpha2Code }} <br>
                Alpha3Code: {{ country.alpha3Code }} <br>
                TopLevelDomain: {{ country.topLevelDomain }} <br>
                Region: {{ country.region }} <br>
                Subregion: {{ country.subregion }} <br>
                Demonym: {{ country.demonym }} <br>
                Timezones: {{ country.timezones }} <br>
                Borders: {{ country.borders }} <br>
                NativeName: {{ country.nativeName }} <br>
                NumericCode: {{ country.numericCode }} <br>
                Currencies: {{ country.currencies }} <br>
                Languages: {{ country.languages }} <br>
                RegionalBlocs: {{ country.regionalBlocs }} <br> -->
              </p>
              <div class="d-flex justify-content-between align-items-center">
                <div class="btn-group">
                  <a :href="country.name" type="button" class="btn btn-sm btn-outline-secondary">
                    View Details</a>                  
                </div>
              </div>
            </div>
          </div>
        </div>    
        <!-- /a single row from an array  -->

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
    mounted(){
            fetch('https://restcountries.eu/rest/v2/all')
            .then(res => res.json())
            .then(data => this.countries = data)
            .catch(err => console.log(err.message))
    }

}
</script>

<style scoped>
.card-img-top {
    width: 100%;
    height: 15vw;
    object-fit: cover;
}
</style>
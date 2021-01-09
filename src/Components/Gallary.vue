<template>
    <div class="container">
      <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">

        <!-- a single row from an array  -->
        <div class="col"  v-for="(country, index) in countries" :key="index">
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
                    <a :href="index" type="button" class="btn btn-sm btn-outline-secondary">
                    View Details</a> 
                </div>
              </div>
            </div>
          </div>
        </div>    
        <!-- /a single row from an array  -->
      </div>
    </div>
     <!-- pagination -->
     <div class="container mt-4">
      <nav aria-label="Page navigation example">
        <ul class="pagination justify-content-center">
          <li class="page-item"><button class="page-link" @click.prevent="previous()">Previous</button></li>
          <li class="page-item"><button class="page-link" @click.prevent="next()">Next</button></li>
        </ul>
      </nav>
     </div>
      <!-- /pagination -->
</template>

<script>
export default {
    data() {
        return {
          totalCounties: 250,
          first: 0,
          last: 12,
          totalInPerPage: 12,
          countries: []
        }
    },
    mounted(){
           this.fetchData()
    },
    methods: {
      fetchData(){
         fetch('https://restcountries.eu/rest/v2/all')
            .then(res => res.json())
            .then(data => this.countries = data.slice(this.first,this.last))
            .catch(err => console.log(err.message))
      },
       previous(){
        this.last = this.first;
        this.first = this.first - this.totalInPerPage;
        if(this.first >= 0){
          this.fetchData()
        }else{
          this.first = 0;
          this.last = this.totalInPerPage;
          this.fetchData()
        }
      },
      next(){
        this.first = this.last;
        this.last = this.last + this.totalInPerPage;
         if(this.last <= this.totalCounties){
          this.fetchData()
        }else{
          this.first = this.totalCounties - this.totalInPerPage;
          this.last = this.totalCounties;
          this.fetchData()
        }
      }
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
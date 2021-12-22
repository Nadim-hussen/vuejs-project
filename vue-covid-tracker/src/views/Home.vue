<template>
  <div class="home">
    <div class="container">
      <div class="row">
<!-- https://documenter.getpostman.com/view/10808728/SzS8rjbc#00030720-fae3-4c72-8aea-ad01ba17adf8 -->
     
      <div class="card1 col-4 mx-auto">
      <h3>Global Data</h3>
      <h5>
       NewConfirmed : {{datacovid.NewConfirmed}}
      </h5>
       <h5>
       NewDeaths : {{datacovid.NewDeaths}}
      </h5>
      
      </div>
      <!-- totol case -->
         <div class="card1 col-4 mx-auto">
      <h3>Global Data</h3>
      <h5>
       TotalConfirmed : {{datacovid.TotalConfirmed}}
      </h5>
       <h5>
       TotalDeaths : {{datacovid.TotalDeaths}}
      </h5>
      
      </div>
      </div>
    </div>
   
  
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  data() {
    return {
      countryname:"",
      datacovid: "",
      datacovidCountry:"",
      title: "Global",
      name:'Nadim'
    };
  },
  components: {},
  methods: {
    async fetchdata() {
      try {
        const res = await fetch("https://api.covid19api.com/summary");
        const data = res.json();
        return data;
      } catch (e) {
        console.log(e);
      }
     
      
    },
  },
  async created() {
    const data = await this.fetchdata();
    this.datacovid = data.Global
    this.countryname = ""
    this.datacovidCountry = data.Countries; 
    // console.log(this.datacovidCountry)
    // const country = this.countryname.find((item)=>{
    //   item.ID === this.datacovidCountry
    // })
    // console.log(country)
  },
};
</script>
 <style scoped>
.home {
  margin: 60px auto;
}
.card1{
  border: 1px solid black;

  height: auto;
}
.card1 h3{
  color: #129488;
}
.card1 h5{
  font-size: 18px;
}
</style>
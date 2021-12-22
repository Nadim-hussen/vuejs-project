<template>
  <div class="home">
    <div class="text-center my-5">
        <h4 class="mb-4">All country Data</h4>
        <div class="w-100 mx-auto">
            <div v-for="value in countryname" :key="value">
                <div class=" row card1 mx-3">
               <h3 class="mt-2  d-flex align-items-stretch">
                   <span class="bold col-2"> Country : {{value.Country}} </span>&nbsp; &nbsp;
                <span class="col-2">NewConfirmed : {{value.NewConfirmed }} </span>  &nbsp; &nbsp;
                <span class="col-2">TotalConfirmed : {{value.TotalConfirmed}} </span>&nbsp; &nbsp;
                 <span class="col-2">NewDeaths : {{value.NewDeaths}} </span>&nbsp; &nbsp;
                  <span class="col-2">TotalDeaths : {{value.TotalDeaths}} </span>
                </h3> 
                </div>
        
     </div>
        </div>

     
     <!-- <template v-for="value in countryname">
    {{value.Country}} : {{value.NewConfirmed}} 
     </template><br /> -->
    </div> 
 </div> 
 
</template>
<script>
import { ref, reactive, toRef, onMounted } from "vue";
export default {
  name: "About",
  setup() {
    const countryname = ref(null);
    
    const fulldata = async () => {
      try {
        const couData = await fetch("https://api.covid19api.com/summary");
        const jsonData = await couData.json();
       
       countryname.value = jsonData.Countries
      
      } catch (e) {
        console.log(e);
      }
    };
    onMounted(() => {
      fulldata();
      console.log();
    });
    return {
      countryname,
     
    };
  },
};
</script>
<style scoped>
.card1 h3 {
  color: #129488;
  font-size: 16px;
}
.card1 {
 border-bottom: 1px solid black;
  height: auto;
}
.bold{
    font-weight: bold;
}
span{
    
    padding: 10px;
}

</style>
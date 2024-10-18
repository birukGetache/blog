<script >
import { ref , reactive, ReactiveEffect , computed, watch, watchEffect} from 'vue';
import TheWelcome from '../components/TheWelcome.vue';
export default{
  components:{
    TheWelcome
  },
  setup (){
    //ref
    const ninjaOne = ref({fathername:"mario" , age:30})

    const updateNinjsOne = () =>{
      ninjaOne.value.age = 40
    }
    const updateNinjsTwo = () =>{
      ninjaTwo.age = 40
    }
    //reactive
    const ninjaTwo= reactive({name:'lugi' , age:35})
    //refs
   const name = ref(null);
   const namePerson = ref('hanni')
   const age = ref(0)
   console.log(name.value)
   const nameinput = ref('');
   const search = ref('');
 const hanlde = ()=>{
  console.log(name.value)
  namePerson.value = "biruk" 
  name.value.classList.add("active");
  name.value.textContent= "hellow ninja"
 }
 const stopwatch = watch(search , ()=>{
   console.log("watch function run when change in search")
 })
 const stopeffect =watchEffect(()=>{
  console.log("watch effect run only when not second argument initailly" , search.value)
 })

 const stop =() =>{
  stopwatch()
  stopeffect()
 }
  const names = ref(["mario ","bura", "helen" , "nati" , "girma", "shuan" , "lugi"])
const matchNames = computed(()=>{
  return names.value.filter((name)=>name.includes(search.value))
})

    return{hanlde , name , namePerson, age , nameinput , ninjaOne , updateNinjsOne, ninjaTwo , updateNinjsTwo ,search , names ,matchNames,stop}
  },
  
  created (){
    console.log("created")
  },
  mounted(){
    console.log("mounted")
  }
  
}
</script>

<template>
 <button @click="hanlde">click me</button>
<button @click="age++">add the age</button>
 <p ref="name">hwllow {{namePerson}}</p>
 <input type="text" v-model="namePerson">
<p>{{ninjaOne.fathername}} - {{ninjaOne.age}}</p>
<button @click="updateNinjsOne">update the age</button>
<button @click="updateNinjsTwo">update the age in ninja Twwo</button>
 <p>nage is {{age}}</p>
 <div>
  <p>ninjaTwo</p>
  <p>{{ninjaTwo.name}} - {{ninjaTwo.age}}</p>
 </div>
 <input type="text" v-model="search">
 <p>start</p>
 <p>{{search}}</p>
 <p>end</p>
 <div v-for="name in matchNames" :key="name">
  <p>{{name}}</p>
 </div>
 <button @click="stop">stop watch</button>
  <main>
    <TheWelcome />
  </main>
</template>
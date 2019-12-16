<template>
  <div>
    <h3>Frontend without css :(</h3>
    <div class= "one-time">
      <h1>One time</h1>
    <input type="date" v-model="date_one"/>
    <p>time</p>
    <input type="time" v-model="time_one"/>
    <button type="submit" @click="submitDay">Submit One time</button>
    </div>
    <div class= "yearly">
      <h1>Yearly</h1>
      <p>Select month</p>
    <select v-model="month">
      
      <option disabled value="Please select one month"></option>
        <option>Jan</option>
        <option>Feb</option>
        <option>Mar</option>
        <option>Apr</option>
        <option>May</option>
        <option>Jun</option>
        <option>Jul</option>
        <option>Aug</option>
        <option>Sep</option>
        <option>Oct</option>
        <option>Nov</option>
        <option>Dec</option>

    </select>
    <p>time</p>
    <input type="time" v-model="time_year"/>
    <button type="submit" @click="submitYearly">Submit Yearly</button>
    </div>
    <div class= "Weekly">
          <h1>Weekly</h1>
      <input type="checkbox" id = "sunday" value="Sunday" v-model="day_select">
          <label for="sunday" >Sunday</label>
          <input type="checkbox" id = "monday" value="Monday" v-model="day_select">
          <label for="monday" >monday</label>
          <input type="checkbox" id = "tuesday" value="Tuesday" v-model="day_select">
          <label for="tuesday" >tuesday</label>
          <input type="checkbox" id = "wednesday" value="Wednesday" v-model="day_select">
          <label for="wednesday" >wednesday</label>
          <input type="checkbox" id = "thursday" value="Thursday" v-model="day_select">
          <label for="thursday" >thursday</label>
          <input type="checkbox" id = "friday" value="Friday" v-model="day_select">
          <label for="friday" >friday</label>
          <input type="checkbox" id = "saturday" value="Saturday" v-model="day_select">
          <label for="saturday" >saturday</label>
          <p>time</p>
        <input type="time" v-model="time_week"/>
        <button type="submit" @click="submitWeekly">Submit Weekly</button>
        </div>
    <div class= "monthly">
      <h1>Monthly</h1> 
    <input type="checkbox" id = "Jan" value="Jan" v-model="month_select">
    <label for="Jan" >Jan</label>
    <input type="checkbox" id = "Feb" value="Feb" v-model="month_select">
    <label for="Feb" >Feb</label>
    <input type="checkbox" id = "Mar" value="Mar" v-model="month_select">
    <label for="Mar" >Mar</label>
    <input type="checkbox" id = "Apr" value="Apr" v-model="month_select">
    <label for="Apr" >Apr</label>
    <input type="checkbox" id = "May" value="May" v-model="month_select">
    <label for="May" >May</label>
    <input type="checkbox" id = "Jun" value="Jun" v-model="month_select">
    <label for="Jun" >Jun</label>
    <input type="checkbox" id = "Jul" value="Jul" v-model="month_select">
    <label for="Jul" >Jul</label>
    <input type="checkbox" id = "Aug" value="Aug" v-model="month_select">
    <label for="Aug" >Aug</label>
    <input type="checkbox" id = "Sep" value="Sep" v-model="month_select">
    <label for="Sep" >Sep</label>
    <input type="checkbox" id = "Oct" value="Oct" v-model="month_select">
    <label for="Oct" >Oct</label>
    <input type="checkbox" id = "Nov" value="Nov" v-model="month_select">
    <label for="Nov" >Nov</label>
    <input type="checkbox" id = "Dec" value="Dec" v-model="month_select">
    <label for="Dec" >Dec</label>
    <p>time</p>
    <input type="time" v-model="time_month"/>
    <button type="submit" @click="submitMonthly">Submit Monthly</button>
    </div>
    <div class= "daily">
      <h1>Daily</h1>
      <p>time</p>
    <input type="time" v-model="time_daily"/>
    <button type="submit" @click="submitDaily">Submit Daily</button>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
    date_one : null,
    time_one : null,
    date_year: null,
    time_year:null,
    time_daily:null,
    month:null,
    time_month:null,
    time_week:null,
    day_select : [],
    month_select : [],
    days: ['sunday','monday','tuesday','wednesday','thursday','friday','saturday']
    }
  },
  methods:{
    submitDay(){
      const headers = {
        'Access-Control-Allow-Origin' : '*',
        'Access-Control-Allow-Methods': 'GET,PUT,POST,DELETE'
      }
      /* eslint-disable no-console */
      // console.log(this.date);
      axios.post('http://localhost:3000/',{"date":this.date_one,"time":this.time_one,"type":"day"},{
        headers:headers
      })
      .then(res=>{
        console.log("data sent")
        console.log(res);
      })
      .catch(err=>{
        console.log(err);
      })

    },
    submitDaily(){
      axios.post('http://localhost:3000/',{"time":this.time_daily,"type":"daily"})
      .then(res=>{
        console.log("data sent")
        console.log(res);
      })
      .catch(err=>{
        console.log(err);
      })

    },
    submitYearly(){
      console.log("tapped")
      axios.post('http://localhost:3000/year',{"month":this.month,"time":this.time_year,"type":"yearly"})
      .then(res=>{
        console.log("data sent")
        console.log(res);
      })
      .catch(err=>{
        console.log(err);
      })

    },
    submitWeekly(){
      axios.post('http://localhost:3000/',{"days":this.day_select,"time":this.time_week,"type":"week"})
      .then(res=>{
        console.log("data sent")
        console.log(res);
      })
      .catch(err=>{
        console.log(err);
      })

    },
    submitMonthly(){
      axios.post('http://localhost:3000/',{"months":this.month_select,"time":this.time_month,"type":"month"})
      .then(res=>{
        console.log("data sent")
        console.log(res);
      })
      .catch(err=>{
        console.log(err);
      })

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<script >
 export default{

  data(){
    return {
        years:"",
        events:[]
    }
  },
  // computed:{
  //   ShowEvents(){
  //     return this.snippet
  //   }
  // },
  methods:{
    async fetchEvents() {
      fetch(`https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=${this.years}&format=json&origin=*`)
  .then(res => res.json())
  .then(data => {
     this.events=data.query.search; 
  });
    },
    stripHTML(html) {
    const div = document.createElement("div");
    div.innerHTML = html;
    return div.textContent || div.innerText || "";
  }
  }
  }
 
</script>

<template>
   <div className="parent">
    <h1>Wikifinder</h1>
    <p>🔍 Search any year or keyword to explore related historical facts and Wikipedia articles!</p>
        <input  placeholder="Enter a year" v-model="years" >
        <button v-if="years!=''" @click="fetchEvents">Get Events</button>
        <table v-if="events.length > 0">
          <thead>
    <tr>
      <th>Title</th>
      <th>Events</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(event, index) in events" :key="index">
      <td>{{ event.title }}</td>
      <td v-html="stripHTML(event.snippet)"></td>
    </tr>
  </tbody>
    </table>
       
    </div>
</template>

<style scoped>
.parent {
  margin: 0 auto;
  width: 1440px;
  text-align: center;
}

h1 {
  margin-top: 8vh;
  font-size: 50px;
}

p {
  font-size: 30px;
}

input {
  margin-top: 20px;
  width: 200px;
  padding: 10px 12px;
  font-size: 20px;
  color: black;
  border: 2px solid #FFC857;
  border-radius: 10px;
  outline: none;
  background: white;
}

button {
  margin-top: 20px;
  margin-left: 20px;
  padding: 10px 12px;
  font-size: 20px;
  color: #fff;
  background-color: #3e0519;
  border: 2px solid rgb(16, 3, 3);
  border-radius: 10px;
  outline: none;
  cursor: pointer;
  transition: transform 500ms ease;
}

button:hover {
  background-color: #fafafa;
  color: #6B370A;
  border: none;
  transform: scale(1.1) translateY(-5px);
}

table {
  width: 100%;
  margin-top: 6vh;
  background-color: #6B370A;
  color: #080303;
  border-collapse: collapse;
}

thead {
  background-color: #FDAF1D;
}

thead tr th {
  padding: 10px;
  font-size: 23px;
  font-weight: bold;
}

table td {
  padding: 15px;
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  border: 1px solid rgb(113, 20, 20);
  outline: none;
}

</style>

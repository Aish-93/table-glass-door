<template>
  <v-container>
    <v-row class="d-flex flex-column justify-content-center">
      <div class="mt-5 text-center"><b>Table-Project </b></div>
      <div class="best" height="400px">
      <thead  >
        <tr >
          <th class="spacers">
            <input type="checkbox" value="checked" id="mycheck" @click="marker" :checked="bean">
             Block</th>
       
          <th class="spacers" @click="sortId" >
            #
          </th>

          <th class="spacers" @click="sorting">Name</th>

          <th class="spacers">Email</th>

          <th class="spacers">Role(s)</th>
 
          <th class="spacers">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(temp, index) in datas" :key="index" class="spacers" @click="picker(index)"
        :class="bean.length > 0 ? 'pick' : '' ">
          <td class="spacers " >
            <input type="checkbox" id="mybox" value="checked"  :checked="dream" ></td>

           
          <td class="spacers">{{ temp.id }}</td>
          <td class="spacers">{{ temp.Name }}</td>
          <td class="spacers">{{ temp.email }}</td>
          <td class="spacers">{{ temp.role }}</td>
          <td class="spacers ">icon</td>
        </tr>
      </tbody>
    </div>
    </v-row>
  </v-container>
</template>
<style lang="scss" scoped>

*{
    box-sizing: border-box;
    margin:0px;
    padding: 0px;
   
}
.pick{
  background-color: rgb(228, 202, 202);
}

.spacers{
    margin:15px;
    padding: 2px 10px 2px 10px ;
    min-width: 180px;
    text-align: center;
    border:2px solid orange;
    

}

</style>
<script>
// import bootstrap from 'bootstrap';
export default {
  data: function() {
    return {
      striker:false,
      bean:'',
      kill:[],
      dream:'',
      datas: [
        {
          id: 1,
          Name: "John",
          email: "john@abc.com",
          role: "Admin Editor Viewer"
        },
        {
          id: 2,
          Name: "Jane",
          email: "jane@abc.com",
          role: "Admin Editor Viewer"
        },
        {
          id: 4,
          Name: "Jim",
          email: "jim@abc.com",
          role: "Viewer"
        },
        {
          id: 3,
          Name: "Sam",
          email: "sam@abc.com",
          role: " Editor Viewer"
        },
        {
          id: 6,
          Name: "Larry",
          email: "larry@abc.com",
          role: " Viewer"
        },
        {
          id: 5,
          Name: "Monica",
          email: "monica@abc.com",
          role: " Editor Viewer"
        }
      ]
    };
  },
  methods:{
    sorting() {
      this.datas.sort(function (a,b){
        var nameA = a.Name.toUpperCase();
        var nameB = b.Name.toUpperCase();

         if (nameA < nameB) {
    return -1;
      }
  if (nameA > nameB) {
    return 1;
  }
      })
      },

      sortId(){
       this.datas.sort(function (a,b){
         return a.id - b.id ;
       })
      },

      marker(){
        this.striker = !this.striker;
        console.log(this.striker);
        if(this.striker === true ){
          this.bean = 'checked';
        }else {
          this.bean ='';
        }

      },
      picker(index){
        this.kill.push(index);
        console.log(this.kill);

      },
      singleMarker(){
        
      },
  }
};
</script>
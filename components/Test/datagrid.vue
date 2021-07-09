                                                                                                                                                      `<template>
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
        <tr v-for="(temp, rowIndex) in datas" :key="rowIndex" class="spacers" 
        :class="{ 'pick': bean.length > 0 , 'ring': select[rowIndex] } ">
          <td class="spacers " >
            <input type="checkbox" id="mybox" :value="select[rowIndex]"
              @click="myFilter(rowIndex)"  :checked="bean"></td>

           
          <td class="spacers" :class="{ active: rowIndex === selected.x && 0 === selected.y}">{{ temp.id }}</td>
          <td class="spacers" :class="{ active: rowIndex === selected.x && 1 === selected.y}">{{ temp.Name }}</td>
          <td class="spacers" :class="{ active: rowIndex === selected.x && 2 === selected.y}">{{ temp.email }}</td>
          <td class="spacers" :class="{ active: rowIndex === selected.x && 3 === selected.y}">{{ temp.role }}</td>
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
.ring{
   background-color: rgb(228, 202, 202);
}
.active {
  border: 2px solid blue !important;
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
// import Direction from 'vue-direction-key'
// Vue.use(Direction)
// import bootstrap from 'bootstrap';
export default {
  data: function() {
    return {
      striker:false,
      bean:'',
      kill:[],
      dream:false,
      select:[],
      selected: {
        x: 0,
        y: 0
      },
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
      myFilter(index){
        // this.$set(this.select, index, !this.select[index])//for only vue
        this.select = this.select.map((selectedItem, _index) => _index === index ? !selectedItem : selectedItem );
        // this.select[index] = !this.select[index];
        console.log(this.select);        
      },
      rows(){
        for(let i = 0; i < this.datas.length; i++){
          this.select.push(false);
          console.log(this.select);
        }
      },
      created: function () {
  // let direction = this.$getDirection()
  
}
  },
  mounted: function() {
    this.rows()
    document.addEventListener('keydown', (e) => {
      console.log('jere', e);
      if (e.key === 'ArrowRight') {
        console.log('here')
        if (this.selected.y === 3){
          this.selected=  {
            x : this.selected.x,
            y: 3
          }
        }else{ 
        this.selected = {
            x : this.selected.x,
            y: this.selected.y + 1
          };
        }

       
      }
      if (e.key === 'ArrowLeft') {
        if(this.selected.y === 0){
          this.selected = {
            x: this.selected.x,
            y: 0
          }
        }else{
        this.selected ={
         x: this.selected.x,

        y: this.selected.y - 1
        }
        }
      }
      if (e.key === 'ArrowUp') {
        if(this.selected.x === 0){
          this.selected={
            x: 0,
            y: this.selected.y
          }
          
        }else{
          this.selected= {
            x:this.selected.x - 1,
            y:this.selected.y
          }
        }
      }
      if (e.key === 'ArrowDown') {
        if(this.selected.x === this.datas.length){
          this.selected.x = this.datas.length
        }else{
        this.selected.x = this.selected.x + 1;}
      }
    })
  },
  
};
</script>
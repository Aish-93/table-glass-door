<template>
  <v-container>
    <v-row class="d-flex flex-column col-12 ">
      <div class="mx-auto"><b>Table-Project </b></div>
      <thead class="spacers">
        <tr >
          <th class="spacers"> Block</th>
       
          <th class="spacers">
            #
          </th>

          <th class="spacers">Name</th>

          <th class="spacers">Email</th>

          <th class="spacers">Role(s)</th>
 class="spacers"
          <th class="spacers">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(temp, index) in datas" :key="index">
          <td><button>icon</button></td>
          <td>{{ temp.id }}</td>
          <td>{{ temp.Name }}}</td>
          <td>{{ temp.email }}</td>
          <td>{{ temp.role }}</td>
          <td>icon</td>
        </tr>
      </tbody>
    
    </v-row>
  </v-container>
</template>
<style lang="scss" scoped>

*{
    box-sizing: border-box;
    margin:0px;
    padding: 0px;
}

.spacers{
    margin:15px;
    padding: 2px 10px 2px 10px ;
}

</style>
<script>
export default {
  data: function() {
    return {
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
          id: 3,
          Name: "Jim",
          email: "jim@abc.com",
          role: "Viewer"
        },
        {
          id: 4,
          Name: "Sam",
          email: "sam@abc.com",
          role: " Editor Viewer"
        },
        {
          id: 5,
          Name: "Larry",
          email: "larry@abc.com",
          role: " Viewer"
        },
        {
          id: 6,
          Name: "Monica",
          email: "monica@abc.com",
          role: " Editor Viewer"
        }
      ]
    };
  }
};
</script>

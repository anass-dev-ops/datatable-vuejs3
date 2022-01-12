<template>
  <div class="home mt-5">
    <h1 class="text-center">Datatable with Vue</h1>
      <div class="container">
                
        <table id="myTable" class="table table-bordered mt-5">
          <thead>
            <tr>
              <th>ID</th>
              <th>User ID</th>
              <th>Title</th>
              <th>Body</th>
            </tr>
          </thead>
          <tbody></tbody>
        </table>

      </div>
  </div>
</template>

<script>
import axios from "axios";
import $ from "jquery";

export default {
  name: 'Home',
  mounted() {
    this.getPosts()
  },
  methods: {
    getPosts() {
      axios.get('https://jsonplaceholder.typicode.com/posts')
      .then((resp) => {
        $("#myTable").DataTable({
          data: resp.data,
            columns: [
              { data: "id" },
              { data: "userId" },
              { data: "title" },
              { data: "body" },
            ],
        })
      })
      .catch((error) => console.log(error.response));

    },
  },
}
</script>

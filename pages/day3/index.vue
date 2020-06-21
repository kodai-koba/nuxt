<template>
  <div class="container">
      <h1>{{message}}</h1>
      
      <div>
        <table class="table table-hover table-striped">
          <thead>
            <tr>
              <th scope="col">Day</th>
              <th scope="col">Discipline</th>
              <th scope="col">Body　Part</th>
              <th scope="col">How</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(post, i) in json_data" :key="i">
              <th scope="row">{{post.userId}}</th>
              <td>{{post.id}}</td>
              <td>{{post.title}}</td>
              <td>{{post.body}}</td>
            </tr>
          </tbody>
        </table>
      </div>
<button type="button" class="btn btn-primary">Instagram</button>
<button type="button" class="btn btn-secondary">Tiwtter</button>
<button type="button" class="btn btn-success">Facebook</button>
<button type="button" class="btn btn-danger">Youtube</button>


<button type="button" class="btn btn-link">Link</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      message: "Fitness blog",
    }
  },
  async asyncData() {
    const url = 'https://jsonplaceholder.typicode.com/posts/'
    const perms = {
        'userId': 11,
        'id': 101,
        'title': 'Leg',
        'body': 'Squat with a barbell'
    }
    const  res   = (await axios.post(url, perms)).data
    const { data } = await axios.get(url)
    data.push(res)
    console.log(res)
    return {
        json_datas: res,
        json_data: data   
   }
 }
}
</script>
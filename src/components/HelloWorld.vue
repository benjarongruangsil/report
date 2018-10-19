<template>
  <div class="">
    <div class="columns">
      <div class="column">
      </div>
      <div class="column">
        <input type="text" name="" value="" v-model="data.id" placeholder="รหัสนักศึกษา" >
      </div>
      <div class="column">
        <input type="text" name="" value="" v-model="data.name" placeholder="ชื่อ">
      </div>
      <div class="column">
        <input type="text" name="" value="" v-model="data.time" placeholder="เวลา">
      </div>
      <div class="column">
        <input type="text" name="" value="" v-model="data.status" placeholder="สถานะ">
      </div>
      <div class="column">
        <input type="text" name="" value="" v-model="data.reason" placeholder="เหตุผล">
      </div>
      <div class="column">
        <button type="button"  name="button" @click="add()">Add</button>
      </div>
      <div class="column">
      </div>
    </div>
    <center>
    <table border="1">
      <tr>
        <td>รหัสนักศึกษา</td>
        <td>ชื่อ</td>
        <td>เวลา</td>
        <td>สถานะ</td>
        <td>เหตุผล</td>
        <td>Delete</td>
      </tr>
      <tr v-for = "(report, key) in show_report">
        <td>{{report.id}}</td>
        <td>{{report.name}}</td>
        <td>{{report.time}}</td>
        <td>{{report.status}}</td>
        <td>{{report.reason}}</td>
        <td><button type="button" name="button" @click="Delete(key)">Delete</button></td>
      </tr>
    </table>
  </center>
  </div>
</template>

<script>
import firebase from 'firebase'
export default {
  data () {
    return {
      data: {
        id: '',
        name: '',
        time: '',
        status: '',
        reason: ''
      },
      show_report: ''
    }
  },
  created: function () {
    this.pullData()
  },
  methods: {
    pullData () {
      let that = this
      firebase.database().ref('/report/').once('value').then(function (snapshot) {
        that.show_report = snapshot.val()
      })
    },
    add () {
      console.log('asd')
      firebase.database().ref('report').push(this.data)
      this.data.id = ''
      this.data.name = ''
      this.data.time = ''
      this.data.status = ''
      this.data.reason = ''
      this.pullData()
    },
    Delete (key) {
      firebase.database().ref('report').child(key).remove()
      this.pullData()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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

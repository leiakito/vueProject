<script setup>
 import {ref} from 'vue'
 let remove = (id,status)=>{
    if(status){
      list.value=list.value.filter(item => item.id!==id)
     }  else {
      alert('请完成学习计划后再进行删除操作')
    }
 }
 const list=ref([
  {
      id: '1',
      subject: 'Vue.js前端实战开发',
      content: '学习指令，例如v-if,v-for,v-model等',
      place: '自习室',
      status: false,
  }, ])
</script>

<template>
  <table class="table table-striped table-hover table-bordered">
    <thead>
      <tr>
        <th scope="col">序号</th>
        <th scope="col">学习科目</th>
        <th scope="col">学习内容</th>
        <th scope="col">学习地点</th>
        <th scope="col">完成状态</th>
        <th scope="col">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in list":key="item.id">
        <td>{{item.id}}</td> 
        <td>{{item.subject}}</td> 
        <td>{{item.content}}</td>
        <td>{{item.place}}</td> 
        <td>
          <div class="form-check form-switch">
            <input class="form-check-input" type="checkbox" role="switch"
            id="flexSwitchCheckDefault" v-model="item.status"/>
            <label class="form-check-label" for="flexSwitchCheckDefault"
            v-if="item.status">已完成</label>
            <label class="form-check-label" for="flexSwitchCheckDefault"
            v-else>未完成</label>
          </div>
        </td> 
        <td>
          <a href="javascript:;"@click="remove(item.id,item.status)">删除</a>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

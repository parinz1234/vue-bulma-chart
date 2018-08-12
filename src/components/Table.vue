<template>
  <div>
    <table 
      class="table is-bordered is-striped is-narrow is-hoverable is-fullwidth"
      >
      <thead>
        <tr>
          <th class="has-text-centered">No</th>
          <th class="has-text-centered">Title</th>
          <th class="has-text-centered">Value</th>
        </tr>
      </thead>
      <tbody>
        <tr :key="item.id" v-for="item in dataList">
          <td>{{item.id}}</td>
          <td>{{item.title}}</td>
          <td>{{item.value}}</td>
          <!-- <td class="has-text-centered" colspan="3">No data</td> -->
        </tr>

      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  props: ['dataList']
}
</script>

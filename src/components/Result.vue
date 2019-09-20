<template>
  <div class="result pt-3">
    <div class="result-container" v-if="entries.length">
      <h3 class="mb-3">Результаты</h3>
      <div class="row">
        <div class="col-12">
          <table class="table table-striped table-bordered">
            <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">Наименование</th>
              <th scope="col">Сумма (тг)</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="(entry, key) in entries" :key="key">
              <th scope="row">{{key + 1}}</th>
              <td>{{entry.name}}</td>
              <td>{{entry.sum}}</td>
            </tr>
            <tr>
              <td class="text-right font-weight-bold" colspan="2">Итого:</td>
              <td class="font-weight-bold">{{totalSum}}</td>
            </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Result',
    props: ['entries'],
    computed: {
      totalSum () {
        let result = 0;
        for (let entry of this.entries) {
          result += parseInt(entry.sum);
        }
        return result;
      }
    }
  }
</script>

<template>
  <div class="row">
    <div class="col-12">
      <div class="form-group">
        <label for="itemName">Введите название</label>
        <input class="form-control" type="text" placeholder="Название" id="itemName" v-model="name"
               @keyup.enter="addEntry">
        <small class="form-text text-danger" v-html="errorName"></small>
      </div>
      <div class="form-group">
        <label for="itemSum">Введите сумму (тг)</label>
        <input class="form-control" type="number" placeholder="Сумма" id="itemSum" v-model="sum"
               @keyup.enter="addEntry">
        <small class="form-text text-danger" v-html="errorSum"></small>
      </div>
      <button class="btn btn-success" @click="addEntry">Добавить</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Entry',
    data () {
      return {
        name: null,
        sum: null,
        errorName: null,
        errorSum: null
      }
    },
    methods: {
      addEntry () {
        if (!this.isValid()) {
          return;
        } else {
          this.errorName = null;
          this.errorSum = null;
        }

        let entry = {
          id: `f${(~~(Math.random() * 1e8)).toString(16)}`,
          name: this.name,
          sum: this.sum
        };

        this.name = '';
        this.sum = '';

        this.$emit('add-entry', entry);
      },
      isValid () {
        if (!this.name) {
          this.errorName = 'Заполните поле Название';
          return false;
        }
        if (!this.sum) {
          this.errorSum = 'Заполните поле Сумма';
          return false;
        }
        return true;
      }
    }
  }
</script>

<template>
  <div>
    <result-card-component title='입력소스' v-bind:code="input"></result-card-component>
    <result-card-component title='출력소스' v-bind:code="result"></result-card-component>
    <result-card-component title='결과소스' v-bind:code="output"></result-card-component>
  </div>
</template>
<script>
import ResultCardComponent from './ResultCardComponent'
export default {
  name: 'show-result-component',
  props: ['row'],
  components: {
    ResultCardComponent
  },
  watch: {
    row: function (n) {
      this.input = n['case_input']
      this.output = n['case_output']
      this.result = n['case_result_user']
    }
  },
  data () {
    return {
      input: '',
      result: '',
      output: ''
    }
  },
  methods: {
    copy (dataName) {
      const t = document.createElement('textarea')
      document.body.appendChild(t)
      t.value = this[dataName]
      t.select()
      document.execCommand('copy')
      document.body.removeChild(t)
    }
  }
}
</script>

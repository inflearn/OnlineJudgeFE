<template>
<Card :bordered="true" style="margin-bottom: 20px">
  <div slot="title">
    <h3>{{ title }}</h3>
    <Button class="right_button" type="info" size="large" @click="copy()">복사하기</Button>
  </div>
  <pre v-highlight="code"><code></code></pre>
</Card>
</template>
<script>

export default {
  name: 'result-card-component',
  props: ['title', 'code'],
  data () {
  },
  methods: {
    copy () {
      const t = document.createElement('textarea')
      document.body.appendChild(t)
      t.value = this.code
      t.select()
      document.execCommand('copy')
      document.body.removeChild(t)
    }
  }
}
</script>
<style scoped>
.right_button {
  position: absolute;
  right: 16px;
  top: 14px;
}
pre {
  border: 1px solid #ddd;
  margin: 0;
}
code {
  max-height: 160px;
  overflow: auto;
}
</style>

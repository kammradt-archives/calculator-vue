<template>
  <vApp>
    <vContainer grid-list-md fill-height>
      <VLayout align-center justify-center text-xs-center>

        <VFlex xs12>
          <h1>Vue.Js Calculator</h1>

          <VLayout wrap>
            <VFlex xs12 md6>
              <VTextField v-model="value0" label="First value" type="number"/>
            </VFlex>
            <VFlex xs12 md6>
              <VTextField v-model="value1" label="Second value" type="number"/>
            </VFlex>
            <VFlex v-for="btn in buttons" :key="btn.label">
              <v-btn color="primary" outline="" block @click="btn.func()">
                {{ btn.label }}
              </v-btn>
            </VFlex>
          </VLayout>
          
          <VDivider class="my-2"/>
          <VFlex v-if="result != null" class="headline">
            Resposta: {{ result }}
          </VFlex>
        </VFlex>
      </VLayout>
    </vContainer>
  </vApp>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      value0: null,
      value1: null,
      result: null,
      buttons:[
        { label:'+', func: this.sum },
        { label:'-', func: this.sub },
        { label:'*', func: this.div },
        { label:'/', func: this.div }
      ]
    }
  },
  methods: {
    sum () {
      if (this.verify()) {
        this.result = parseInt(this.value0) + parseInt(this.value1)
      }
    },
    sub () {
      if (this.verify()) {
        this.result = parseInt(this.value0) - parseInt(this.value1)
      }
    },
    mult () {
      if (this.verify()) {
        this.result = parseInt(this.value0) * parseInt(this.value1)
      }
    },
    div () {
      if (this.verify()) {
        this.result = parseInt(this.value0) / parseInt(this.value1)
      }
    },
    verify () {
      if (this.value0 && this.value1) {
        return true
      }
      return false
    }
  },
}
</script>

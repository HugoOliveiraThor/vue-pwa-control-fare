<template>
    <b-container class="bv-example-row">
      <b-row>
        <b-col style="display:flex;flex-direction: column;}">
            <label for="input-live">Nome</label>
            <span for="input-live">{{form.name || '-'}}</span>
        </b-col>
        <b-col>
            <label for="input-live">Data da corrida</label>
            <datetime
            v-model="form.date"
            zone="America/Sao_Paulo"
            >
            </datetime>
        </b-col>
        <b-col sm="1" lg="1">
         <b-form-checkbox
           id="ida"
           v-model="form.ida"
           name="ida"
           :value="true"
           :unchecked-value="false"
           >
           Ida
        </b-form-checkbox>
        </b-col>
        <b-col sm="1" lg="1">
         <b-form-checkbox
           id="volta"
           v-model="form.volta"
           name="volta"
           :value="true"
           :unchecked-value="false"
           >
           Volta
        </b-form-checkbox>
        </b-col>
      </b-row>
    </b-container>
</template>

<script>
export default {
  name: 'control-user',
  props: {
    form: {
      type: Object,
      required: false,
      default: () => {
        return {
          name: '',
          date: new Date(),
          ida: true,
          volta: false
        }
      }
    }
  },
  data () {
    return {
      date: new Date()
    }
  }
}
</script>

<style lang="scss" scoped>

</style>

<template>
    <b-container class="bv-example-row" style="padding-top:20px;">
      <b-row>
        <b-col style="display:flex;flex-direction: column;}" sm='1' lg='1' >
            <label for="input-live">Nome</label>
            <span for="input-live">{{form.name || '-'}}</span>
        </b-col>
        <b-col>
            <label for="input-live">Data da corrida</label>
            form-{{form}}
            <datetime
            v-model="form.dateOfTheRide"
            @change.native="onChange"
            format="dd-MM-yyyy"
            zone="America/Sao_Paulo"
            >
            </datetime>
        </b-col>
        <b-col sm="1" lg="1">
         <b-form-checkbox
           :id="$uuid.v1()"
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
           :id="$uuid.v1()"
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
import moment from 'moment'
export default {
  name: 'control-user',
  props: {
    form: {
      type: Object,
      required: false,
      default: () => {
        return {
          name: '',
          dateOfTheRide: moment().format('YYYY-MM-DDTHH:mm:ss.SSSZ'),
          ida: true,
          volta: false
        }
      }
    }
  },
  computed: {
    getDate () {
      let date = new Date()
      return date.toString()
    }
  },
  mounted () {
    // console.log(date)
    // this.form.date = date.toString()
    // console.log('OLAAAA', this.form)
  },
  data () {
    return {
      dataTeste: ''
    }
  },
  methods: {
    onChange () {
      console.log('Alterou', this.form)
    }
  },
  watch: {
    form: {
      deep: true,
      immediate: true,
      handler (val) {
        console.log('val', val)
      }
    }
  }
}
</script>

<style lang="scss" scoped>

</style>

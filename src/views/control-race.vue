<template>
  <b-container>
    <control-user :form="{name:'Hugo', dateOfTheRide:defaultDate}"></control-user>
    <control-user :form="{name:'Alex', dateOfTheRide:defaultDate}"></control-user>
    <control-user :form="{name:'Irwing', dateOfTheRide:defaultDate}"></control-user>
    <b-row>
      <b-col style="padding-top:20px;">
      <b-button variant="outline-primary" @click="() => save()">Gravar dados</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import moment from 'moment'
const dateRide = moment().format('YYYY-MM-DDTHH:mm:ss.SSSZ')
export default {
  components: {
    'control-user': () => import('@/components/control-user')
  },
  data () {
    return {
      form: {
        email: '',
        name: '',
        food: null,
        checked: []
      },
      foods: [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
      show: true,
      defaultDate: dateRide
    }
  },
  methods: {
    onSubmit (evt) {
      evt.preventDefault()
      alert(JSON.stringify(this.form))
    },
    save () {

    },
    onReset (evt) {
      evt.preventDefault()
      // Reset our form values
      this.form.email = ''
      this.form.name = ''
      this.form.food = null
      this.form.checked = []
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>

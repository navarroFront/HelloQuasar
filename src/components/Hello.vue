<template>
<div>
  <q-layout>
    <!-- Header -->
    <div slot="header" class="toolbar">
      <q-toolbar-title :padding="1">
        Breda's Sistemas
      </q-toolbar-title>
    </div>

    <!-- Footer -->
    <div slot="footer" class="toolbar">
      <button class="secondary push" @click="batteryCall">status bateria</button>
    </div>


  </q-layout>
</div>
</template>

<script>
import {
  Toast,
  Dialog
} from 'quasar'
export default {
  data() {
    return {

    }
  },
  methods: {
    batteryCall() {

      addEventListener('batterystatus', onBatteryStatus, false)

      function onBatteryStatus(status) {

        Toast.create({

          html: 'Nível' + status.level + ' isPlugged: ' + status.isPlugged,
          icon: 'alarm_add',
          timeout: 10000,
          color: '#f8c1c1',
          bgColor: 'green',
          button: {
            label: 'Bateria',
            handler() {
              // Specify what to do when button is clicked/tapped
            },
            color: '#000'
          },
          vm: {
            // VueModel for the Toast
          }
        })

        // Dialog.create({
        //   title: 'Bateria',
        //   message: 'Nível' + status.level + ' isPlugged: ' + status.isPlugged,
        //   buttons: [
        //     'OK',
        //     {
        //       label: '---',
        //       handler() {
        //         // empty the trash bin, yo
        //       }
        //     }
        //   ]
        // })

      }
    }
  }
}
</script>

<style lang="styl">
.toolbar{
  justify-content:center
}

#view-flexbox
  margin-top 30px
  max-width 95vw
  .row, .column, .flex
    > div > div
      padding 10px
      border-radius 3px
      background rgba(147, 128, 108, .1)
      text-align center
  &.with-border
    .row, .column, .flex
      border 2px solid teal
      > div
        border 1px dashed orange
</style>

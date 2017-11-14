<template>
  <v-app id="inspire">
      <v-navigation-drawer
        v-model="drawer"
        app
        fixed
      >
        <v-list dense>
          <v-list-tile @click="">
            <v-list-tile-action>
              <v-icon>fa-microchip</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Node1</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
          <v-list-tile @click="">
            <v-list-tile-action>
              <v-icon>fa-microchip</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Node2</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-navigation-drawer>
      <v-toolbar color="cyan" dark fixed app>
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title>Monitoring</v-toolbar-title>
      </v-toolbar>
      <v-content>

    </v-layout>
    </br>
    <v-layout>
      <v-flex d-flex xs12 >
        <v-card color="blue-grey darken-2" class="white--text" >
          <v-card-title primary-title>
            <div>
              <h2 class="headline mb-0">{{value.node}}</h2>
            </div>
          </v-card-title>
        </v-card>
      </v-flex>
      <v-flex d-flex xs6 >
        <v-card>
          <v-card-title primary-title>
            <div>
              <h3 class="headline mb-0">OnlineNow</h3>
              <div><h1>{{value.onlinenow}}</h1></div>
              <div>
                <h3>Devices</h3>
              </div>
            </div>
          </v-card-title>
        </v-card>
      </v-flex>


    </v-layout>
</br>
<v-layout>

<v-flex d-flex xs6 >
  <v-card >
    <v-card-title primary-title>
      <div>
        <h3 class="headline mb-0">Download</h3>
        <div >
          <v-progress-circular
            v-bind:size="100"
            v-bind:width="15"
            v-bind:rotate="90"
            v-bind:value="value.speedtestDown"
            color="green"
            >
            <h3>{{value.speedtestDown}}</h3> Mb/s
          </v-progress-circular>
        </div>
      </div>
    </v-card-title>
  </v-card>
</v-flex>

<v-flex d-flex xs6 >
  <v-card>
    <v-card-title primary-title>
      <div>
        <h3 class="headline mb-0">Upload</h3>
        <div >
          <v-progress-circular
            v-bind:size="100"
            v-bind:width="15"
            v-bind:rotate="90"
            v-bind:value="value.speedtestUp"
            color="green"
            >
            <h3>{{value.speedtestUp}}</h3> Mb/s
          </v-progress-circular>
        </div>
      </div>
    </v-card-title>
  </v-card>
</v-flex>



</v-layout>
</br>
<v-layout>
  <v-flex d-flex xs6 >
    <v-card>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Inbound</h3>
          <div><h3>{{value.inbound}} Mb</h3></div>

        </div>
      </v-card-title>
    </v-card>
  </v-flex>

  <v-flex d-flex xs6 >
    <v-card>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Outbound</h3>
          <div><h3>{{value.outbound}} Mb</h3></div>
        </div>
      </v-card-title>
    </v-card>
  </v-flex>
</v-layout>

</br>
<v-layout>
  <v-flex d-flex xs6 >
    <v-card>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Packetloss</h3>
        </br><div><h2>{{value.packetloss}} </h2></div>

        </div>
      </v-card-title>
    </v-card>
  </v-flex>

  <v-flex d-flex xs6 >
    <v-card>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Utilization</h3>
          <div><h3>{{value.utilize}} %</h3></div>
          <v-progress-linear value="value.utilize" height="20" color="info"></v-progress-linear>
        </div>
      </v-card-title>
    </v-card>
  </v-flex>
</v-layout>

      </v-content>
      <v-footer color="cyan" app>
        <span class="white--text">&copy; Wipoo $ Panya </span>
      </v-footer>
    </v-app>
</template>

<script>
// import dashboard from './components/dashboard'
import {Data} from './components/firebase'

export default {
  data: () => ({
    drawer: false,
    value: ''
  }),
  props: {
    source: String
  },
  created () {
    setTimeout(() => {
      var vm = this
      let getData = this.dataTouse.find(datas => datas.node === 'Node1')
      console.log(getData)
      vm.value = getData
    }, 3000)
  },
  firebase: {
    dataTouse: Data
  }
}
</script>


<style lang="scss">
 @import './styles/font.scss';
</style>

<style lang="stylus">
@import './styles/main';
</style>

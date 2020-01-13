<template>
  <v-app>

    <div v-if="$route.name === 'freetalking_beginner'">
      <v-layout>

        <v-navigation-drawer v-model="drawer" :mini-variant="mini" absolute style="background-color:#5C8D89; position:fixed; top:0; left:0; overflow-y:scroll;" temporary>

          <v-list class="pa-1">
            <v-list-tile avatar>
              <v-list-tile-avatar>
                <img src="http://cdn.onlinewebfonts.com/svg/img_97686.png">
              </v-list-tile-avatar>

              <v-list-tile-content>
                <v-list-tile-title>Free Talking Step 1</v-list-tile-title>
              </v-list-tile-content>


            </v-list-tile>
          </v-list>

          <v-divider></v-divider>
          <v-list>

            <template v-slot:activator>
              <v-list-tile>
                <v-list-tile-action>
                  <v-icon>book</v-icon>
                </v-list-tile-action>
                <v-list-tile-title>Table of Contents</v-list-tile-title>
              </v-list-tile>
            </template>

            <v-list class="custom-list">
              <v-list-tile>
                <h2>Table of Contents</h2>
              </v-list-tile>
              <v-list-tile @click="$router.push('/freetalking/beginner/chapter' + n)" v-for="n in 40" :key="n">Chapter {{n}}</v-list-tile>

            </v-list>
          </v-list>
        </v-navigation-drawer>

        <v-toolbar app :fixed="toolbar.fixed" :clipped-left="toolbar.clippedLeft" style="background-color: #5C8D89;">
          <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
          <v-toolbar-title style="margin-left: 0px; margin-right: 5px;">Free Talking Step 1</v-toolbar-title>
          <v-spacer></v-spacer>

          <template v-if="speechSlot" #extension>
            <v-container>
              <v-row>
                <v-toolbar-items>
                  <v-col cols="4">
                    <v-icon @click="textToSpeech()" class="ml-5" large color="black">{{icon}}</v-icon>
                  </v-col>
                  <v-spacer></v-spacer>
                  <v-col cols="4">
                    <v-icon @click="stopSpeech()" large color="black">stop</v-icon>
                  </v-col>
                  <v-spacer></v-spacer>
                  <v-col cols="4">
                          <v-menu offset-y>
                            <template v-slot:activator="{ on }">
                              <v-btn v-on="on" depressed block text color="#5C8D89">{{speechRateText}}</v-btn>
                            </template>
                            <v-list>
                              <v-list-item>
                                <v-list-item-title class="mx-2" @click="changeSpeechRate($event)"><center>0.5x</center></v-list-item-title>
                              </v-list-item>
                                <v-divider></v-divider>
                              <v-list-item>
                                <v-list-item-title  class="mx-2"  @click="changeSpeechRate($event)"><center>1x</center></v-list-item-title>
                              </v-list-item>
                              <v-divider></v-divider>
                              <v-list-item>
                                <v-list-item-title  class="mx-2" @click="changeSpeechRate($event)"><center>1.5x</center></v-list-item-title>
                              </v-list-item>
                            </v-list>
                          </v-menu>
                  </v-col>
                </v-toolbar-items>
              </v-row>
            </v-container>
          </template>



          <!--  <v-menu v-model="speechInfo" offset-y offset-x>
          <template v-slot:activator="{ on }"> -->
          <v-icon v-on="on" color="black" @click="speechSlot = !speechSlot" large>volume_up</v-icon>
          <!--  </template>
          <v-card width="50" height="50">
          hi
        </v-card>
      </v-menu>  -->





      <v-menu min-width="100%" offset-y>
        <template v-slot:activator="{ on }" style="min-width:100%;">
          <v-toolbar-title v-on="on">
            <span>ᴀA</span>

          </v-toolbar-title>
        </template>

        <v-list style="overflow-y: hidden;">
          <v-list-tile>
            <v-slider v-model="fontSize" :min="15" :max="30" :step="1"></v-slider>
          </v-list-tile>
        </v-list>

      </v-menu>

    </v-toolbar>
  </v-layout>

</div>




<div v-if="$route.name === 'freetalking_intermediate'">
  <v-layout>


    <v-navigation-drawer v-model="drawer" :mini-variant="mini" absolute style="background-color:#c38b8b; position:fixed; top:0; left:0; overflow-y:scroll;" temporary>


      <v-list class="pa-1">
        <v-list-tile avatar>
          <v-list-tile-avatar>
            <img src="http://cdn.onlinewebfonts.com/svg/img_97686.png">
          </v-list-tile-avatar>

          <v-list-tile-content>
            <v-list-tile-title>Free Talking Step 2</v-list-tile-title>
          </v-list-tile-content>

        </v-list-tile>
      </v-list>

      <v-divider></v-divider>
      <v-list>

        <template v-slot:activator>
          <v-list-tile>
            <v-list-tile-action>
              <v-icon>book</v-icon>
            </v-list-tile-action>
            <v-list-tile-title>Table of Contents</v-list-tile-title>
          </v-list-tile>
        </template>

        <v-list class="custom-list">
          <v-list-tile>
            <h2>Table of Contents</h2>
          </v-list-tile>
          <v-list-tile @click="$router.push('/freetalking/intermediate/chapter' + n)" v-for="n in 20" :key="n">Chapter {{n}}</v-list-tile>

        </v-list>

      </v-list>
    </v-navigation-drawer>

    <v-toolbar app :fixed="toolbar.fixed" :clipped-left="toolbar.clippedLeft" style="background-color: #c38b8b;">
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title style="margin-left: 0px; margin-right: 5px;">Free Talking Step 2</v-toolbar-title>
      <v-spacer></v-spacer>

      <template v-if="speechSlot" #extension>
        <v-container>
          <v-row>
            <v-toolbar-items>
              <v-col cols="4">
                <v-icon @click="textToSpeech()" class="ml-5" large color="black">{{icon}}</v-icon>
              </v-col>
              <v-spacer></v-spacer>
              <v-col cols="4">
                <v-icon @click="stopSpeech()" large color="black">stop</v-icon>
              </v-col>
              <v-spacer></v-spacer>
              <v-col cols="4">
                      <v-menu offset-y>
                        <template v-slot:activator="{ on }">
                          <v-btn v-on="on" depressed block text color="#c38b8b">{{speechRateText}}</v-btn>
                        </template>
                        <v-list>
                          <v-list-item>
                            <v-list-item-title class="mx-2" @click="changeSpeechRate($event)"><center>0.5x</center></v-list-item-title>
                          </v-list-item>
                            <v-divider></v-divider>
                          <v-list-item>
                            <v-list-item-title  class="mx-2"  @click="changeSpeechRate($event)"><center>1x</center></v-list-item-title>
                          </v-list-item>
                          <v-divider></v-divider>
                          <v-list-item>
                            <v-list-item-title  class="mx-2" @click="changeSpeechRate($event)"><center>1.5x</center></v-list-item-title>
                          </v-list-item>
                        </v-list>
                      </v-menu>
              </v-col>
            </v-toolbar-items>
          </v-row>
        </v-container>
      </template>

      <v-icon v-on="on" color="black" @click="speechSlot = !speechSlot" large>volume_up</v-icon>

      <v-menu min-width="100%" offset-y>
        <template v-slot:activator="{ on }" style="min-width:100%;">
          <v-toolbar-title v-on="on">
            <span>ᴀA</span>

          </v-toolbar-title>
        </template>



        <v-list style="overflow-y: hidden;">
          <v-list-tile>
            <v-slider v-model="fontSize" :min="15" :max="30" :step="1"></v-slider>
          </v-list-tile>
        </v-list>

      </v-menu>




    </v-toolbar>
  </v-layout>



</div>


<div v-if="$route.name === 'patterncourse_adultbasic'">
  <v-layout>

    <v-navigation-drawer v-model="drawer" :mini-variant="mini" absolute style="background-color:#9692af; position:fixed; top:0; left:0; overflow-y:scroll;" temporary>

      <v-list class="pa-1">
        <v-list-tile avatar>
          <v-list-tile-avatar>
            <img src="http://cdn.onlinewebfonts.com/svg/img_97686.png">
          </v-list-tile-avatar>

          <v-list-tile-content>
            <v-list-tile-title>Pattern Course Adult Basic Step 1</v-list-tile-title>
          </v-list-tile-content>


        </v-list-tile>
      </v-list>

      <v-divider></v-divider>
      <v-list>

        <template v-slot:activator>
          <v-list-tile>
            <v-list-tile-action>
              <v-icon>book</v-icon>
            </v-list-tile-action>
            <v-list-tile-title>Table of Contents</v-list-tile-title>
          </v-list-tile>
        </template>

        <v-list class="custom-list">
          <v-list-tile>
            <h2>Table of Contents</h2>
          </v-list-tile>
          <v-list-tile @click="$router.push('/pattercourse/adultbasic/chapter' + n)" v-for="n in 40" :key="n">Chapter {{n}}</v-list-tile>

        </v-list>
      </v-list>
    </v-navigation-drawer>

    <v-toolbar app :fixed="toolbar.fixed" :clipped-left="toolbar.clippedLeft" style="background-color: #9692af;">
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title style="margin-left: 0px; margin-right: 5px;">Pattern Course Adult Basic Step 1</v-toolbar-title>
      <v-spacer></v-spacer>

      <template v-if="speechSlot" #extension>
        <v-container>
          <v-row>
            <v-toolbar-items>
              <v-col cols="4">
                <v-icon @click="textToSpeech()" class="ml-5" large color="black">{{icon}}</v-icon>
              </v-col>
              <v-spacer></v-spacer>
              <v-col cols="4">
                <v-icon @click="stopSpeech()" large color="black">stop</v-icon>
              </v-col>
              <v-spacer></v-spacer>
              <v-col cols="4">
                      <v-menu offset-y>
                        <template v-slot:activator="{ on }">
                          <v-btn v-on="on" depressed block text color="#9692af">{{speechRateText}}</v-btn>
                        </template>
                        <v-list>
                          <v-list-item>
                            <v-list-item-title class="mx-2" @click="changeSpeechRate($event)"><center>0.5x</center></v-list-item-title>
                          </v-list-item>
                            <v-divider></v-divider>
                          <v-list-item>
                            <v-list-item-title  class="mx-2"  @click="changeSpeechRate($event)"><center>1x</center></v-list-item-title>
                          </v-list-item>
                          <v-divider></v-divider>
                          <v-list-item>
                            <v-list-item-title  class="mx-2" @click="changeSpeechRate($event)"><center>1.5x</center></v-list-item-title>
                          </v-list-item>
                        </v-list>
                      </v-menu>
              </v-col>
            </v-toolbar-items>
          </v-row>
        </v-container>
      </template>

      <v-icon v-on="on" color="black" @click="speechSlot = !speechSlot" large>volume_up</v-icon>

      <v-menu min-width="100%" offset-y>
        <template v-slot:activator="{ on }" style="min-width:100%;">
          <v-toolbar-title v-on="on">
            <span>ᴀA</span>

          </v-toolbar-title>
        </template>

        <v-list style="overflow-y: hidden;">
          <v-list-tile>
            <v-slider v-model="fontSize" :min="15" :max="30" :step="1"></v-slider>
          </v-list-tile>
        </v-list>

      </v-menu>

    </v-toolbar>
  </v-layout>

</div>







<router-view :fontSize="fontSize"></router-view>


</v-app>
</template>

<script>
import Speech from 'speak-tts'
import Vue from 'vue'
export default {



  data() {
    return {
      drawer: null,
      pathname: window.location.pathname,
      items: [{
        title: 'Home',
        icon: 'dashboard'
      },
      {
        title: 'About',
        icon: 'question_answer'
      }
    ],
    mini: false,
    right: null,

    toolbar: {
      //
      fixed: true,
      // sets if the toolbar contents is leaving space for drawer (false) or not (true)
      clippedLeft: false,

    },
    icon: 'play_arrow',
    speech: new Speech(),
    stop_button: false,
    selectedString: '',
    speechRateText: '1x',
    speechRate: 1,



    fontSize: 15,

    speechInfo: true,
    speechSlot: false,


  }
},

watch: {

  fontSize(current, old) {





  }
},
mounted() {
  this.speech.cancel()
  console.log(this.pathname)

},
methods: {

  textToSpeech() {

    var string = this.$el.innerText
    var string2

    if(this.speechRate == 0.75 || this.speechRate == 1.25 ){
      string2 = string.slice(528, string.length).trim().replace(/\s/g,' ')
    }else if(this.speechRate == 1){
      string2 = string.slice(526, string.length).trim().replace(/\s/g,' ')
    }

    this.speech.init({
      volume: 1,
      lang: "en-US",
      rate: this.speechRate,
      pitch: 1,

    }).then((data) => {

    }).catch(e => {})

    this.speech.setVoice('Google US English')

    this.speech.speak({
      text: string2.trim()
    }).then(() => {
      console.log("Success !")
    }).catch(e => {
      console.error("An error occurred :", e)
    })

    if (this.speech.speaking()) {

      document.addEventListener('mouseup', event => {
        this.selectedString = event.target.innerText
        console.log(this.selectedString != "play_arrow" && this.selectedString != "pause" && this.selectedString != "0.5X" && this.selectedString != "1X" && this.selectedString != "1.5X")
        if(this.selectedString != "play_arrow" && this.selectedString != "pause" && this.selectedString != "0.5X" && this.selectedString != "1X" && this.selectedString != "1.5X" && this.selectedString != "0.5x" && this.selectedString != "1x" && this.selectedString != "1.5x"){
          this.speech.cancel();
          this.selectedTextToSpeech()
        }

        if(this.selectedString == "play_arrow"){
        console.log('resume')
        this.speech.resume()
        this.icon = "pause";
      }else if(this.selectedString == "pause"){
      console.log('pause')
      this.speech.pause()
      this.icon = "play_arrow";
    }

  })

  Vue.set(this.$data, 'icon', 'pause')

}else{
  if(this.selectedString == "pause"){
    this.speech.pause()
    this.icon = "play_arrow"
  }else if(this.selectedString == "play_arrow"){
    this.speech.resume()
    this.icon = "pause"
  }
}
},

stopSpeech() {
  Vue.set(this.$data, 'icon', 'play_arrow')
  this.speech.cancel()
},

selectedTextToSpeech() {

  if (!this.speech.speaking()) {

    this.speech.init({
      volume: 1,
      lang: "en-US",
      rate: this.speechRate,
      pitch: 1,

    }).then((data) => {}).catch(e => {})
    console.log(this.selectedString)
    this.speech.speak({
      text: this.selectedString,
      listeners: {
        onend: () => {
          Vue.set(this.$data, 'icon', 'play_arrow')
        }
      }
    }).then(() => {
      console.log("Success !")
    }).catch(e => {
      console.error("An error occurred :", e)
    })

    /*
    if(this.selectedString == "pause"){
    this.speech.pause()
    this.icon = "play_arrow"
  }else if(this.selectedString == "play_arrow"){
  this.speech.resume()
  this.icon = "pause"
}*/

Vue.set(this.$data, 'icon', 'pause')

}



},

changeSpeechRate(selected){
  this.speechRateText = selected.target.innerText

  if(selected.target.innerText == "0.5x"){
    this.speech.setRate(0.75)
    this.speechRate = 0.75
  }
  if(selected.target.innerText == "1x"){
    this.speech.setRate(1)
      this.speechRate = 1
  }
  if(selected.target.innerText == "1.5x"){
    this.speech.setRate(1.25)
      this.speechRate = 1.25
  }
}

}



}
</script>

<style>
.custom-list {
  max-height: 100vh;
  overflow-y: scroll;
}
</style>

<template>
  <v-container>
    <v-card class="justify-center align-center mx-auto mt-6 pa-10">
            <v-img
              :src="require('@/assets/encrypt.jpeg')"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="400px"
            >
              <v-card-title>Simple Web application for Encryption and Decryption</v-card-title>
            </v-img>
    <v-row align="center" justify="center" class="mt-3">
      <v-icon
      large
      @click="swaplabel"
      color="grey darken-2">
      mdi-swap-horizontal-bold
    </v-icon>
    </v-row>
      <v-row align="center" justify="center">
        <v-col cols="6">
        <v-textarea
          v-model="inputtext"
          filled
          name="input-7-4"
          :label="inputlabel"
          :prepend-inner-icon="inputicon"
        ></v-textarea>
        </v-col>
        <v-col cols="6">
        <v-textarea ref="cipher"
          v-model="outputext"
          filled
          name="input-7-4"
          :label="outputlabel"
          :prepend-inner-icon="outputicon"
          disabled
        ></v-textarea>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
  export default {
      data() {
    return {
      inputtext:"",
      outputext:"",
      inputlabel:"Plain Text",
      outputlabel:"Cipher Text",
      inputicon:"mdi-clipboard-text-outline",
      outputicon:"mdi-lock"
    };
  },
  methods:{
    convert(s){
      var i=0;
      var t="";
      for(i=0;i<s.length;i++){
      if(s[i]==" "){
      t+=" ";
      }
      else if(s[i]==s[i].toUpperCase()){
      t+=String.fromCharCode(25+65*2-s.charCodeAt(i));
      }
      else{
      t+=String.fromCharCode(25+97*2-s.charCodeAt(i));
      }
      }
      return t;    
  },
  swaplabel(){
    var temp=this.inputlabel;
    this.inputlabel=this.outputlabel;
    this.outputlabel=temp;
    temp=this.inputicon;
    this.inputicon=this.outputicon;
    this.outputicon=temp;
    this.inputtext=this.outputext;
  }

  },
  watch:{
    inputtext:function(){
      this.outputext=this.convert(this.inputtext);
    }
  }
  }
</script>

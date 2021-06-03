<template>
    <div>
        <div class="headtop">
            <P>The best sustainable products to help you buy good...now shipping in the UK</P>
        </div>
        <div class="container-fluid divimage">
            <div class="row">
                <div class="col-sm-3">
                    <img src="@/assets/drlogo.png" alt="dayrize logo" class="daylogo">
                </div>
                <div class="col-sm-6">
                    <h1 class="title">Photos that inspire</h1>
                </div>
                <div class="col-sm-3">
                    <img src="@/assets/drlogo.png" alt="dayrize logo" class="daylogo">
                </div>
            </div>
        </div>
        <div class="container mainbody">
            <div class="row rowarrow">
                <div class="col-sm-3 fa1 farleft">
                    <div class="row">
                        <div class="col-sm-6">
                            <img src="@/assets/person2.png" alt="dayrize logo" class="personpic2">
                        </div>
                        <div class="col-sm-6">
                            <i @click="prev" class="fa fa-chevron-circle-left fa-4x" aria-hidden="true"></i>
                        </div>
                    </div>
                </div>
                <div class="col-sm-6 imgthingy">
                    <div v-for="number in [currentNumber]" :key='number' >
                        <img :src="[[posts[number].url]]" class="imgcar" />
                    </div> 
                </div>
                <div class="col-sm-3 fa1 faright">
                    <div class="row">
                        <div class="col-sm-6">
                            <i @click="next" class="fa fa-chevron-circle-right fa-4x" aria-hidden="true"></i>
                        </div>
                        <div class="col-sm-6">
                            <img src="@/assets/person.png" alt="dayrize logo" class="personpic">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios"

export default {
    name: "Home",
   data(){
         return{
             posts: [],
             currentNumber: 0
         } 
     },
     created: function (){

        axios.get("https://jsonplaceholder.typicode.com/albums/1/photos")
              .then(response => {this.posts = response.data})
              
          },
computed: {
currentImage: function() {
return this.posts[Math.abs(this.currentNumber) % this.posts.length];
}
},
 methods: {
        next: function() {
            this.currentNumber += 1
        },
        prev: function() {
            this.currentNumber -= 1
        }
    },

}
</script>

<style scoped>
.headtop{
    font-weight: bold;
    font-size: 25px;
    background-color: #e5e8d5;
    padding-top: 10px;
}
.divimage{
    padding-top: 10px;
    background-color: #ffffff;
    padding-bottom: 15px;
}
.title{
    font-size: 90px;
}
.daylogo{
    width: 40%;
    height: auto;
}
.mainbody{
    width: 100%;
    height: 100vh;
    background-color: #e5e8d5;
    padding: 50px 0;
}
.imgcar{
    width: 600px;
    height: 600px;
    border-radius: 40px;
    border: solid 15px #ffdb00;
}
.divpics{
    padding-top: 30px;
}
.divquery{
    display: flex;
    justify-content: center;
    align-items: center;
}
.picdis{
    font-weight: bold;
    font-size: 25px;
}
.fa-chevron-circle-left{
    margin-right: 100px;
}
.fa-chevron-circle-right{
    margin-left: 100px;
}
.fa{
    color: #ffdb00;
}
.fa1{
    margin-top: 300px;
}
.personpic{
    margin-top: -200px;
    width: 200px;
    height: auto;
}
.personpic2{
    margin-top: -200px;
    width: 200px;
    height: auto;
    margin-left: -50px;
}
</style>
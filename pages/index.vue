<template>
  <div data-app>
    <!-- Home -->
    <div id="home">
      <div>
        <v-app-bar dark class="nav_bar">
          <div class="appbar_content">
            <ul>
              <li><a href="#home">HOME </a></li>
              <li><a href="#about"> ABOUT </a></li>
              <li><a href="#product"> COLLECTION </a></li>
              <li><a href="#contact">CONTACT </a></li>
            </ul>
          </div>

          <v-spacer />

       
        </v-app-bar>
        
        <template>
          <div>
            
            <v-parallax
              height="700"
              :src="require('../static/uploads/cover.jpg')"
            >
            <img :src="a[4].img"  width="100px" class="logo_web">
              <div>
                <v-icon class="menu" style="color:white" @click="openNav()"
                  >mdi-menu</v-icon
                >
                <!-- <span class="menu" style="color:white" @click="openNav()">&#9776;</span> -->
              </div>
              <div id="mySidenav" class="sidenav" close-on-content-click>
                <a
                  href="javascript:void(0)"
                  class="closebtn"
                  @click="closeNav()"
                  >&times;</a
                >
                <a href="#" @click="closeNav()">Home</a>
                <a href="#about" @click="closeNav()">About</a>
                <a href="#product" @click="closeNav()">Collection</a>
                <a href="#contact" @click="closeNav()">Contact</a>
              </div>

              <div class="cover_text ">
                <img
                  :src="a[4].img"
                  class="logo_bef"
                  height="100"
                  width="100"
                />
                <h1 style="margin-top:10%">
                  {{ a[3].Content }}
                </h1>
              </div>
              <div class="btn_cover">
                <v-btn height="50px" width="150px" outlined href="#about"
                  >LEARN MORE</v-btn
                >
              </div>
            </v-parallax>
          </div>
        </template>
      </div>
    </div>

    <!--About div -->
    <div class="overlay_1">
      <div class="about_us " id="about">
        <div class="container">
          <h2 style="margin-top:5rem">
            ABOUT US
          </h2>
                       <div v-html="$md.render(a[0].Content)"></div>

        </div>
      </div>
    </div>
    <!-- Product Div -->
    <div class="products" id="product">
      <div class="container prod">
        <div class="text_products">
          <h3>COLLECTIONS</h3>
          <h1>{{ a[2].Content }}</h1>
        </div>
        <div>
          <!-- <LightGallery
            :images="
              articles.map((article, index) => {
                return {
                  title: article.description,
                  url: article.img
                };
              })
            "
            :index="index"
            :disable-scroll="true"
            @close="index = null"
          /> -->
          <template>
            <v-row justify="center">
              <v-dialog light v-model="dialog" max-width="490">
                <template v-slot:activator="{ on, attrs }">
                  <div
                    dark
                    v-bind="attrs"
                    v-on="on"
                    class="image"
                    v-for="(image, i) in articles"
                    :key="i"
                    @click="() => img_dialog(i)"
                  >
                    <img :src="image.img" height="300px" width="300px" />
                    <figcaption class="centered">
                      {{ image.title }}
                    </figcaption>
                  </div>
                </template>
                <v-card class="mx-auto" max-width="1000">
                  <v-img
                    :src="articles[h].img"
                    height="auto"
                    max-height="365px"
                    min-height="270px"
                  >
                    <!-- <div>
                    <v-btn @click="dialog=false" style="float:right; left:5%; background:black" >
                    <v-icon  >mdi-close</v-icon> </v-btn>
                    </div> -->
                    <v-btn
                      v-if="h < articles.length - 1"
                      @click="img_next(h)"
                      style="float:right;  top:90%; background:black;opacity:0.2;"
                      ><v-icon> mdi-arrow-right </v-icon>
                    </v-btn>
                    <v-btn
                      v-if="h > 0"
                      @click="img_prev(h)"
                      style="float:left; right:100%; top:90%; background:black;opacity:0.2"
                    >
                      <v-icon> mdi-arrow-left </v-icon>
                    </v-btn>
                  </v-img>

                  <v-card-title> {{ articles[h].title }} </v-card-title>

                  <!-- <v-card-subtitle>
                    1,000 miles of wonder
                  </v-card-subtitle> -->

                  <v-card-actions>
                    <v-btn style="color:green" text>
                      Explore
                    </v-btn>

                    <v-spacer></v-spacer>

                    <v-btn icon @click="show = !show">
                      <v-icon>{{
                        show ? "mdi-chevron-up" : "mdi-chevron-down"
                      }}</v-icon>
                    </v-btn>
                  </v-card-actions>

                  <v-expand-transition>
                    <div v-show="show">
                      <v-divider></v-divider>

                      <v-card-text>
                                      <div v-html="$md.render(articles[h].description)"></div>
                      </v-card-text>
                    </div>
                  </v-expand-transition>
                  <v-btn block style="color:red" @click="dialog = false">
                    CLOSE
                  </v-btn>
                </v-card>
              </v-dialog>
            </v-row>
          </template>
        </div>
      </div>
    </div>

    <!-- Contact us -->
    <div class="overlay">
      <div class="contact " id="contact">
        <div class="container text_contact ">
          <h3>Contact</h3>
          <h1>Get In Touch.</h1>
        </div>
        <v-row>
          <v-col>
            <div class="form_cont center">
              <form
                method="POST"
                name="contactForm"
                data-netlify="true"
                class="form_cont"
              >
                <input type="hidden" name="form-name" value="contactForm" />
                <v-container class="form_container">
                  <p style="align-text:center">SEND US A MESSAGE</p>
                  <v-row>
                    <v-col cols="12" xs="12" sm="6" md="6" lg="6">
                      <input
                        class="col"
                        type="text"
                        color="white"
                        placeholder="Name"
                        outlined
                        name="name"
                        required
                      />
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col cols="12" xs="12" sm="3" md="3" lg="3">
                      <input
                        class="col"
                        outlined
                        type="text"
                        placeholder="Email"
                        name="email"
                        required
                      />
                    </v-col>
                    <v-col cols="12" xs="12" sm="3" md="3" lg="3">
                      <input
                        class="col"
                        type="text"
                        outlined
                        placeholder="Subject"
                        name="subject"
                        required
                      />
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col cols="12" xs="12" sm="6" md="6" lg="6">
                      <textarea
                        class="col"
                        type="message"
                        outlined
                        placeholder="Message"
                        name="message"
                      />
                    </v-col>
                  </v-row>

                  <v-row>
                    <v-col cols="12" xs="12" sm="6" md="6" lg="6">
                      <v-btn block type="submit" class="btn_submit"
                        >Submit</v-btn
                      >
                    </v-col>
                  </v-row>
                </v-container>
              </form>
            </div>
          </v-col>
        </v-row>
      </div>
    </div>
    <template>
      <v-footer
        style="text-align:center; margin:0px; padding:0px; background:black "
        :padless="padless"
      >
        <v-card flat dark tile width="100%" class="red lighten-1 text-center">
          <v-card-text>
            <a :href="'//' + x[0].link" target="_blank">
              <v-icon size="24px">
                mdi-facebook
              </v-icon>
            </a>
            <a :href="'//' + x[1].link" target="_blank" icon>
              <v-icon size="24px">
                mdi-instagram
              </v-icon>
            </a>
          </v-card-text>

          <v-divider></v-divider>

          <v-card-text class="white--text">
            Copyright © GOLO Handicrafts 2020.
          </v-card-text>
        </v-card>
      </v-footer>
    </template>
  </div>
</template>

<script>
import contactform from "../components/contactform";
import footer from "../components/footer";
import about from "../content/post/about.md";
import covertext from "../content/post/covertext.md";
import collectiontext from "../content/post/collectiontext.md";
import logo from "../content/post/logo.md";
import "vue-blueimp-gallery/dist/vue-blueimp-gallery.css";
import gallery from "vue-blueimp-gallery";
// import VueGallery from "vue-gallery";
import { LightGallery } from "vue-light-gallery";

export default {
  async asyncData(context) {
    const { $content } = context;
    const articles = await $content("product").fetch();
    const a = await $content("post").fetch();
    const x = await $content("socialmedia").fetch();
    x: x.sort((x, y) => x.id - y.id);
    console.log(articles.length);
    return {
      articles,
      a: a.sort((a, b) => a.id - b.id),
      x: x.sort((x, y) => x.id - y.id)
    };
  },
  watch: {
    h: function(val) {}
  },



  components: {
    contactform,
    footer,
    gallery,
    LightGallery
  },
  data() {
    return {
      index: null,
      bar: false,
      dialog: false,
      h: 1,
      show: false,
      padless: false,
      icons: [
        { image: "mdi-facebook", url: "facebook.com" },
        { image: "mdi-instagram", url: "instagram.com" }
      ],

      origin: null
    };
  },
  methods: {

    //next image
    img_next(a) {
      a = a + 1;
      this.h = a;
    },
//previous image
    img_prev(a) {
      a = a - 1;
      this.h = a;
    },
   //open image dialog 
    img_dialog(a) {
      this.dialog = true;

      this.h = a;
      return this.h;
    },
//sidenav for mobile view
    openNav() {
      document.getElementById("mySidenav").style.width = "250px";
    },

    closeNav() {
      document.getElementById("mySidenav").style.width = "0";
    },

    tooglenav() {
      $(".appbar_content");
    }
  }
};
</script>
<style lang="scss">
.btn_cover {
  color: white !important;
}
.v-parallax_content {
  height: 200vh !important;
  width: 100%;
  opacity: 1;
  overflow: hidden;
}

.v-parallax__image {
  height: 1800px !important;
  min-height: 400px !important;
  min-width: 50% !important;
  width: 100% !important;
}
.container {
  min-height: max-content !important;
}
.burger {
  display: none;
}
.logo_web{
  margin-top:-25%
}
.logo_bef {
  display: none;
}
.overlay {
  /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#6b4da8+0,4977c2+100&0.85+0,0.85+100 */

  // background: url("../assets/contact-bg.jpg"),
  //   -moz-linear-gradient(left, rgba(107, 77, 168, 0.85) 0%, rgba(
  //           73,
  //           119,
  //           194,
  //           0.85
  //         )
  //         100%); /* FF3.6-15 */
  // background: url("../assets/contact-bg.jpg"),
  //   -webkit-linear-gradient(left, rgba(107, 77, 168, 0.85) 0%, rgba(
  //           73,
  //           119,
  //           194,
  //           0.85
  //         )
  //         100%); /* Chrome10-25,Safari5.1-6 */
  // // background: url("../assets/contact-bg.jpg"),
  //   linear-gradient(
  //     to right,
  //     rgba(107, 77, 168, 0.85) 0%,
  //     rgba(73, 119, 194, 0.85) 100%
  //   ); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#d96b4da8', endColorstr='#d94977c2', GradientType=1 );
  background-blend-mode: overlay;
  background-color: rgb(32, 23, 23) !important;
  /* IE6-9 */
}
.overlay_1 {
  background: -moz-linear-gradient(
    left,
    rgba(107, 77, 168, 0.85) 0%,
    rgba(73, 119, 194, 0.85) 100%
  ); /* FF3.6-15 */
  background: -webkit-linear-gradient(
    left,
    rgba(107, 77, 168, 0.85) 0%,
    rgba(73, 119, 194, 0.85) 100%
  ); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(
    to right,
    rgba(107, 77, 168, 0.85) 0%,
    rgba(73, 119, 194, 0.85) 100%
  ); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#d96b4da8', endColorstr='#d94977c2', GradientType=1 );
  background-blend-mode: overlay;
  /* IE6-9 */
}
.centered {
  position: relative;
  background: black;
  opacity: 0.3;
  color: white;
  //  border: 2px solid #ebebeb;
  text-transform: uppercase;
  top: 0%;
  left: 0.1%;
  transform: translate(0.4%, -30%);
  // visibility: hidden;
}
.nav_item a {
  text-align: center !important;
  align-content: center;
  padding: 10px;
  margin: 10px;
}
.cover_card {
  align-items: center;
  text-align: center;
  color: grey !important;
}

.appbar_content {
  background: transparent !important;
  background-color: Transparent;
  background-repeat: no-repeat;
  border: none;
  cursor: pointer;
  overflow: hidden;
  display: flex;
}
.form_container {
  margin-left: 25%;
}

.pro_card {
  cursor: pointer;
  text-align: center !important;
}
.image {
  float: left;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center center center;
  border: 1px solid #ebebeb;
  margin-left: 50px;
  margin-top: 2%;
  height: 300px;
  width: 300px;
  margin-bottom: 2%;

  cursor: pointer;
}

.image:hover {
  transform: scale(1.1) !important;
  // transition-delay: 0.1s !important;

  transition: all 0.5s;
  transition-property: all;
  transition-duration: 0.5s;
  transition-timing-function: ease;
  transition-delay: 0s;
}

.pro_card div {
  text-align: center;
}
.pro_card:hover .centered {
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
a {
  text-decoration: none;
}
.appbar_content ul {
  margin: 0;
  padding: 0;
  display: flex;
}
.appbar_content {
  align-content: center;
  text-align: center;
  display: flex;
}
.appbar_content li {
  list-style: none !important;
}
.appbar_content li a {
  text-decoration: none;
  color: white;
  padding: 2rem;
}
.nav_bar li:hover {
  background: #818181;
}
* {
  box-sizing: border-box;
}

.home {
  height: 150vh;
}

.about_us {
  font-family: "montserrat-bold", sans-serif;
  text-align: center;
  background: rgb(32, 23, 23) !important;

  color: white;
  min-height: 70vh;
  height: max-content;
}
.about_us p {
  font-family: "librebaskerville-bold", serif;
  font-size: 3rem;
  line-height: 1.8;
  color: white;
  margin-top: 5rem;
}
.cover_text {
  text-align: center;
  font-family: "montserrat-bold", sans-serif;
  font-size: 2.2rem;
  color: white;
  text-transform: uppercase;
  margin-top: -5% !important;
  letter-spacing: 0.3rem;
  margin: 0 0 0.9rem 0;
  padding: 10%;
}

.logo {
  display: block;
  position: center center center center;

  margin: 0;
  padding: 0;
  outline: 0;
  border: none;
  // height: 190px !important;
  width: 100px !important;
  // height: 37px;
  margin-top: -20%;
  background-size: 190px 165px;
  font: 0/0 a;
  text-shadow: none;
  color: transparent;
  transition: all 0.5s ease-in-out;
}
.btn_cover {
  align-content: center;
  color: white !important;
  text-align: center;
  margin-top: -10%;
  background: transparent !important;
}
.theme--light.v-btn {
  color: white;
}

.products {
  background: #e9e9e9;
  align-content: center;
  text-align: center;
  color: black;
  min-height: 100vh;
  height: max-content;
  display: flex;
  // margin-bottom: 2%;
}
.products .container {
  margin-bottom: 2%;
}
.products h3,
.text_contact h3 {
  color: black;
  font-family: "montserrat-bold", sans-serif;
  font-size: 1.8 rem;
  line-height: 1.667;
  // color: rgba(242, 242, 242, 0.5);
  text-transform: uppercase;
  letter-spacing: 0.3rem;
  margin-bottom: 1.2rem;
}
.text_contact h3 {
  color: white !important;
}
.products h1 {
  color: black;
  font-family: "librebaskerville-bold", serif;
  font-size: 2.8rem;
  line-height: 1.375;
  display: block;
  padding-left: 17%;
  padding-right: 17%;
}
.text_products {
  color: #000000;
  padding: 8%;
  justify-content: center;
}
.text_contact {
  align-content: center;
  text-align: center;
}
.text_contact h1 {
  font-family: "librebaskerville-bold", serif;
  font-size: 2.8rem;
  line-height: 1.375;
  display: block;
}
.contact {
  color: white;
  padding: 7%;
  align-content: center !important;
  align-items: center;
  min-height: 100vh;
  min-height: max-content;
  justify-items: center;
}

.menu {
  font-size: 20px !important;
  display: none !important;
  cursor: pointer;
  margin-top: -15% !important;
  float: right;
  position: fixed;
  // background: rgba(0, 0, 0, 0.4);
}
.menu_btn {
  background: transparent !important;
  height: 42px !important;
  margin-top: -2%;

  float: right;
  position: fixed;
  display: block;
}

.sidenav {
  height: 100%;
  width: 0;

  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: #111;
  overflow-x: hidden;
  transition: 0.5s;
  padding-top: 60px;
}

.sidenav a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

.sidenav a:hover {
  color: #f1f1f1;
}

.sidenav .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}
.responsive {
  width: 100%;
  opacity: 1;
  height: auto;
  max-height: 250px;
  display: block;
  max-width: 350px;
  transition: transform 0.2s;
}

.responsive:hover {
  transform: scale(1.2);
  transition-delay: 0.1ms;
}

html {
  scroll-behavior: smooth;
}
.form_contact {
  align-items: center;
  float: center;
  align-self: center;
}
.btn_submit {
  background: transparent !important;
  font-size: 1.5rem;
  display: block;
  letter-spacing: 0.2rem;
  height: 6rem;
  line-height: 6rem;
  padding: 0 3rem;
  width: 100%;
  background: #f9a828 !important;
  color: #000000;
  margin-top: 0.6rem;
}

v-form h3 {
  font-size: 1.4rem;
  line-height: 1.7;
  text-transform: uppercase;
  letter-spacing: 0.2rem;
}

v-text-field {
  border: white !important;
  color: white !important;
}
v-form input,
textarea {
  background: white !important;
}
input,
v-textarea {
  background: white !important;
}
@media screen and (max-width: 580px) {
  .image:hover {
    transform: unset !important;

    transition: unset !important;
  }
}
@media screen and (max-height: 450px) {
  .sidenav {
    padding-top: 15px;
  }
  .sidenav a {
    font-size: 18px;
  }
}
@media only screen and (min-width: 150px) {
  h1,
  .products h1,
  .contact h1 {
    font-size: 30px;
  }
  h3 {
    font-size: 30px;
  }
  .v-parallax__image {
    height: 1800px !important;
   
    // min-height: 20% !important;
    min-width: 50% !important;
    // max-width: 250px !important;
    width: 100% !important;
  }

  .about_us p {
    font-size: 25px;
  }
  .menu {
    font-size: 30px;
    cursor: pointer;
    // margin-top: 10%;
    // margin-left: -50%;
    float: right;
    position: fixed;
    // background: rgba(0, 0, 0, 0.4);
  }
  img {
    max-width: auto;
    max-height: auto;
    min-width: auto;
    min-height: auto;
  }
  v-card:hover {
    cursor: pointer;
  }
}
@media only screen and (max-width: 600px) {
  .nav_bar v-btn {
    width: 30px !important;
  }
}

@media only screen and (max-width: 550px,) {
  .logo {
    height: auto;
    width: auto;
    // max-width: 50px;
    min-width: 80px !important;
  }
}
@media only screen and (min-width: 550px) and (max-width: 1024px) {
  .image:hover {
    transform: scale(1.2) !important;
    transition-delay: 0.1ms !important;
  }
}

@media only screen and (max-width: 700px) and (min-width: 150px) {
  .appbar_content {
    display: none !important;
  }
  .logo_web{
    display: none !important;
  }
  .logo_bef {
    display: inline !important;
  }
  .nav_bar {
    display: none !important;
  }
  .menu {
    font-size: 30px !important;
    display: inline !important;
    cursor: pointer;
    // margin-top: -40% !important;
    float: right;
    position: absolute !important;
    // background: rgba(0, 0, 0, 0.4);
  }
  .menu_btn {
    // background: transparent !important;
    height: 42px !important;
    margin-top: -2%;

    float: right;
    position: fixed;
    display: block;
  }
}
.logo {
  height: 100px;
  width: 100px;
}
.nav_bar {
  // display: flex;
  justify-content: space-between;
  // align-items: center;
  align-items: flex-end;
}
@media only screen and (max-width: 600px) {
  .form_cont {
    margin-left: -15% !important;
    margin-right: 10%;
  }
}
@media only screen and (max-width: 400px) {
  .image {
    margin-left: 25px !important ;
    margin-bottom: 7% !important;
  }
}
@media only screen and (max-width: 420px) {
  .image {
    margin-left: 45px !important ;
    margin-bottom: 7% !important;
  }
}
@media only screen and (max-width: 380px) {
  .image {
    margin-left: 25px !important ;
    margin-bottom: 7% !important;
  }
}

@media only screen and (max-width: 322px) {
  .image {
    height: auto;
    width: auto;
    margin-bottom: 7% !important;

    margin-top: 3%;
    // padding-right: 60px;
  }
}
@media only screen and (max-width: 370px) {
  .image {
    margin-left: 15px !important ;
    margin-bottom: 7% !important;
  }
}

@media only screen and (max-width: 320px) {
  .image {
    height: auto;
    width: auto;
    margin-left: -3px !important;
    margin-top: 3%;
    margin-bottom: 7% !important;

    // padding-right: 60px;
  }

  .text_products h3 {
    font-size: 20px;
  }
  .text_products h1 {
    font-size: 22px;
  }
  .about_us h2 {
    font-size: 20px;
  }
  .about_us .container p {
    font-size: 12px;
  }
  .cover_text h1 {
    font-size: 25px;
  }
}
@media only screen and (max-width: 281px) {
  .image {
    margin-left: -35px !important;
    margin-top: 3%;
    margin-bottom: 7% !important;

    // padding-right: 60px;
  }
  .text_products h3 {
    font-size: 20px;
  }
  .text_products h1 {
    font-size: 22px;
  }
  .about_us h2 {
    font-size: 20px;
  }
  .about_us .container p {
    font-size: 12px;
  }
  .cover_text h1 {
    font-size: 25px;
  }
}
//logo
@media only screen and (min-width: 701px) and (max-width: 820px) {
.logo_web{
  margin-top:-45% !important;
}

}
@media only screen and (min-width: 821px) and (max-width: 1060px) {

.logo_web{
  margin-top: -35% !important;
}
}
@media only screen and (min-width: 1061px) and (max-width: 1590px) {
.logo_web{
  margin-top: -20% !important;
}
}


@media only screen and (max-width: 550px) {
  .form_cont {
    margin-left: -10% !important;
    margin-right: 15%;
  }
  .about_us p {
    font-size: 20px !important;
    // text-align: justify;;
  }
}
@media only screen and (max-width: 350px) {
  .container {
    min-height: max-content !important;
  }
}
@media only screen and (max-width: 550px) {
  .image {
    margin-left: 110px;
    margin-bottom: 7% !important;
  }

  .appbar_content {
    display: none;
  }
  .logo_bef {
    display: inline !important;
  }
  .nav_bar {
    display: none;
  }
  .menu {
    font-size: 30px !important;
    display: inline !important;
    cursor: pointer;
    margin-top: -25% !important;
    float: right;
    position: absolute !important;
  }
  .menu_btn {
    height: 42px !important;
    margin-top: -2%;

    float: right;
    position: fixed;
    display: block;
  }
}
@media screen and (max-width: 400px) {
  .appbar_content {
    display: none;
  }
  .logo_bef {
    display: inline !important;
  }
  .nav_bar {
    display: none;
  }
  .menu {
    font-size: 30px !important;
    display: inline !important;
    cursor: pointer;
    margin-top: -40% !important;
    float: right;
    position: absolute !important;
    // background: rgba(0, 0, 0, 0.4);
  }
  .menu_btn {
    height: 42px !important;
    margin-top: -2%;

    float: right;
    position: fixed;
    display: block;
  }
}
@media screen and (max-width: 325px) {
  .image {
    margin-left: -2px;
    margin-bottom: 7% !important;
  }
}
.blueimp-gallery .control.button.close {
  margin: 0.3rem;
  color: #e9e9e9 !important;
  cursor: pointer;
  width: 30% !important;
}
.blueimp-gallery .control.button.caption-edit,
.blueimp-gallery .control.button.remove {
  display: none !important;
}
</style>

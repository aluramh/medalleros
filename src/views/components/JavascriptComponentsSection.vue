<template>
  <div class="wrapper">
    <div id="javascriptComponents">
      <div class="title">
        <h2>Javascript components</h2>
      </div>
      <div class="md-layout">
        <div class="md-layout-item md-small-size-100">
          <div class="title">
            <h3>Modal</h3>
          </div>
          <div class="md-layout">
            <div class="md-layout-item md-size-33">
              <md-button @click="classicModal = true" class="md-success md-block">
                <md-icon>library_books</md-icon>Classic
              </md-button>
              <modal @close="classicModalHide" v-if="classicModal">
                <template slot="header">
                  <h4 class="modal-title">Modal Title</h4>
                  <md-button
                    @click="classicModalHide"
                    class="md-simple md-just-icon md-round modal-default-button"
                  >
                    <md-icon>clear</md-icon>
                  </md-button>
                </template>

                <template slot="body">
                  <p>
                    Far far away, behind the word mountains, far from the
                    countries Vokalia and Consonantia, there live the blind
                    texts. Separated they live in Bookmarksgrove right at the
                    coast of the Semantics, a large language ocean. A small
                    river named Duden flows by their place and supplies it with
                    the necessary regelialia. It is a paradisematic country, in
                    which roasted parts of sentences fly into your mouth. Even
                    the all-powerful Pointing has no control about the blind
                    texts it is an almost unorthographic life One day however a
                    small line of blind text by the name of Lorem Ipsum decided
                    to leave for the far World of Grammar.
                  </p>
                </template>

                <template slot="footer">
                  <md-button class="md-simple">Nice Button</md-button>
                  <md-button @click="classicModalHide" class="md-danger md-simple">Close</md-button>
                </template>
              </modal>
            </div>
          </div>
        </div>
      </div>
      <br>

      <div class="title">
        <h3>Carousel</h3>
      </div>

      <div class="md-layout">
        <div class="md-layout-item md-size-75 mx-auto md-small-size-100">
          <md-card>
            <carousel
              :autoplay-timeout="5000"
              :mouse-drag="false"
              :per-page="1"
              :speed="700"
              autoplay
              loop
              navigationEnabled
              navigationNextLabel="<i class='material-icons'>keyboard_arrow_right</i>"
              navigationPrevLabel="<i class='material-icons'>keyboard_arrow_left</i>"
            >
              <template v-for="({ image, caption }) in images">
                <slide :key="image">
                  <div class="carousel-caption" v-if="caption">
                    <h4>{{caption}}</h4>
                  </div>

                  <img :src="image" alt="carousel1">
                </slide>
              </template>
            </carousel>
          </md-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Modal } from "@/components";
const carousel1 = require("@/assets/img/nature-2.jpg");
const carousel2 = require("@/assets/img/nature.jpg");
const carousel3 = require("@/assets/img/nature-3.jpg");

export default {
  components: {
    Modal
  },
  data() {
    return {
      classicModal: false,
      selectedDate: new Date("2018/03/26"),
      images: [
        { image: carousel1, caption: "This is a caption" },
        { image: carousel2 },
        { image: carousel3 },
        { image: carousel1 },
        { image: carousel1 }
      ]
    };
  },
  methods: {
    classicModalHide() {
      this.classicModal = false;
    }
  }
};
</script>

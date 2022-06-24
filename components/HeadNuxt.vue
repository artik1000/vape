<template>
  <v-card class="overflow-hidden">
    <v-app-bar
      absolute
      color="black"
      dark
      shrink-on-scroll
      prominent
      src="https://i.pinimg.com/564x/94/9e/df/949edfc7a714523628913e9ee5d4e3cc.jpg"
      fade-img-on-scroll
      scroll-target="#scrolling-techniques-3"
    >
      <template #img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(64,69,69,.7), rgba(34,29,17,.7)"
        />
      </template>

      <v-app-bar-nav-icon />

      <v-app-bar-title>Vape Panda</v-app-bar-title>

      <v-spacer />

      <v-btn icon>
        <v-icon>mdi-cart</v-icon>
      </v-btn>

      <v-btn icon>
        войти
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-login-variant</v-icon>
      </v-btn>

      <template #extension>
        <v-tabs
          v-model="tab"
          align-with-title
        >
          <v-tabs-slider color="white" />

          <v-tab
            v-for="(itemos, ig) in items"
            :key="ig"
            @click="currentShow(ig)"
          >
            {{ itemos.bname }}
          </v-tab>
        </v-tabs>
      </template>
    </v-app-bar>
    <v-sheet
      id="scrolling-techniques-3"
      class="overflow-y-auto"
      max-height="90vh"
    >
      <v-container style="height: max-content;" fluid>
        <v-main v-if="slideractiveu">
          <v-tabs-items v-model="tab" height="70vh" class="vtb">
            <v-tab-item
              v-for="itemss in screenslide"
              :key="itemss.id"
            >
              <v-card
                color="basil"
                flat
              >
                <v-card-text>
                  <v-carousel
                    cycle
                    hide-delimiters
                    hide-delimiter-background
                    show-arrows-on-hover
                  >
                    <template #prev="{ on, attrs }">
                      <v-btn
                        v-ripple="false"
                        height="50vh"
                        width="47vw"
                        style="margin-top:-40vh; border: none;box-shadow: none;"
                        color="transparent"
                        class="buttonsoncar"
                        v-bind="attrs"
                        v-on="on"
                      >
                        <v-icon class="iconright">
                          mdi-arrow-collapse-left
                        </v-icon>
                      </v-btn>
                    </template>
                    <template #next="{ on, attrs }">
                      <v-btn
                        v-ripple="false"
                        height="50vh"
                        width="47vw"
                        style="margin-top:-40vh; border: none;box-shadow: none;"
                        color="transparent"
                        class="buttonsoncar"
                        v-bind="attrs"
                        v-on="on"
                      >
                        <v-icon class="iconleft">
                          mdi-arrow-collapse-right
                        </v-icon>
                      </v-btn>
                    </template>
                    <v-carousel-item
                      v-for="(itema,i) in screenslide"
                      :key="i"
                      :src="itema.url"
                    />
                  </v-carousel>
                </v-card-text>
              </v-card>
            </v-tab-item>
          </v-tabs-items>
        </v-main>
        <v-main v-if="top">
          <v-row
            style="margin-top: 30vh;"
          >
            <TopGoods
              v-for="hit in hits"
              :key="hit.id"
            />
          </v-row>
        </v-main>
        <v-main
          v-if="shop"
        >
          <v-row style="margin-top: 30vh;">
            <v-col cols="3">
              <ShopNuxt />
            </v-col>
            <v-col cols="9">
              <v-row>
                <TopGoods
                  v-for="hit in hits"
                  :key="hit.id"
                />
              </v-row>
            </v-col>
          </v-row>
        </v-main>
      </v-container>
    </v-sheet>
  </v-card>
</template>

<script>
import TopGoods from '@/components/TopGoods'
import ShopNuxt from '@/components/ShopNuxt'
export default {
  components: {
    TopGoods, ShopNuxt
  },
  data () {
    return {
      slideractiveu: true,
      top: false,
      shop: false,
      screenslide: [],
      items: [
        { id: 0, bname: 'Новинки' },
        { id: 1, bname: 'Акции' },
        { id: 2, bname: 'Хиты продаж' },
        { id: 3, bname: 'Магазин' }
      ],
      dete: 'Новинки',
      bonus: [
        { id: 0, name: 'Акции', url: 'https://htmlcolorcodes.com/assets/images/colors/navy-blue-color-solid-background-1920x1080.png', completed: false },
        { id: 1, name: 'Акции', url: 'https://www.solidbackgrounds.com/images/1920x1080/1920x1080-spanish-sky-blue-solid-color-background.jpg', completed: false },
        { id: 2, name: 'Акции', url: 'data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBw0HBwcHCA0ICAcHBw0HBwcHCA8ICQcNIBEiIiARExMYHSggGCYlGxUfITEhJSkrLi4uFx8zODMsNygtLisBCgoKDQ0NDg0NDysZFRkrKysrLSsrKzctKysrKy0rKysrNzcrLS0rLSsrKysrKystKysrKysrKysrKysrKysrK//AABEIAKgBLAMBIgACEQEDEQH/xAAZAAADAQEBAAAAAAAAAAAAAAABAgMABQT/xAAYEAEBAQEBAAAAAAAAAAAAAAAAEQESAv/EABkBAQEBAQEBAAAAAAAAAAAAAAABAgQDBv/EABYRAQEBAAAAAAAAAAAAAAAAAAARAf/aAAwDAQACEQMRAD8A7GafNSzT5r6J86rmmzUs02azqq5p81LNNmoK5ps1LNNmsxVc0+almmzWVUzTVLNHNQWzRzUs02akFaNSzRqRVc0ekqNSCuaPSXQ9JFU6bpPpqQU6ap9NSClCkrUgehuk6DpYh90tLuhVgahS0KRB3Q3S7pd1YDul3Q3Q3WkHdLQoVUczNNmpZps10QVzT5qOabNZiq5p81HNNmpBbNNmo5ps1mC2ejZqGejZqRVqbNRz0bPSQVz0bNRzTdMwVo9JdD0kVXoekum6ILdN0lR6SCtap9N0RVK3SfTdEFKFJ0HRBSh0n0HREU30FJQqwPQ3SUKsD76Lvou6XdWIahuloVYg7oUu6FWDmZps1LNPmuhFM02anmmzWVUzTZqVHNSC2aNSzTVmCmafNRzTZqQVzRqWabpIqueh6So56SCueh6SrdJBboekum6ILdN0l0PSRVem6TrVIKdN0nWqwU6CkrUgehSUKQUoUlCrA++g6JQpA+6FJQqxD0KTdCrEPS0N0tWDmZp81HNPmuiIrmmzUs0c1mKrRqeaOakFc0anRzUgrmjmpZps1BXNGpUazFUo1PoaQUzRqdGpBTNHNSps1IK1qnRpFUrdJ9NUgp01TrUgpW6TrUgfoKWhVgehSVqQPQpK1WBqFLQpENWpKFUNuhS0KsRzM02almmzXRBXNNmpZps1mCtHNSzTZqQUzRzU80akFc01SzRzUgrWqdGpBSjUqNSCtHpKtSKtnoc1LNHNSCtGpUakVStU+mpBStU61IKVqn03RBStU+m6IHrUnQUgehukrVYGrUlCrEPQpK1IG3Qpd0K1Bzc02almmzXvEVzRzU80azBSjU6NSCmabPSVHNSCtGpUc9JBXoanWqQUo9J1qQV6GpVqkFs0c1LPQ9EFeh6Sz0NSKpWqdGkFKFJWqQPWpKFWClap1qQUoUlDogpQpK1WBq1JQpA9CloVYHoUlarBzs0c1PNNmvZlTNNmpU1SKpWzU6OagpRqdGgpRqdGoHo0laoKVqSjSB80anRqQUo1OjmpBSj0nWqQU6bpOjSKp03SdakFK1TrdED1qTpqsD0KStSB61TrUgehS0KsD1qStSBqFLQqo5+abNSzTZr2RXNGp5o1BStSZo1FPRpK1QUo1OjUD0anRoKUanRqQUrUlakFK1JRqQPRqdakFK1To0gfpqStSClCkrUinrUlagehS0KB61JWqhq1LWoGrUlakQ1aloVRz80c0maNeiKUanRoKUanRqClGp1qiqUanRqB6OanRqClGp0aB6NJWoKVqStQUrVOjQPRqdagpWpKFBStU6NFPWpK1A9CloUD1qStRDVqWhVgetSVqQNQoUKo8Gaap5o1tFM0anmjUD0aStQPRpKNRT5o1PNGoHo1OjUFM0anmjQUo1OtUFK1JRoGo0lagejU61BStU61BStU6NUPWpK1A9CloUD1qStQNRpK1UNWpK1WIahS1qQeLNHNZmg2azMgLVmAaLMDUazIDmszIotWYBo1mQajWYBrVmQatWZQK1ZgajWZRq1ZgahRYArVmUaszAFasyo1CswP/9k=', completed: false }
      ],
      novelty: [
        { id: 0, name: 'Новинки', url: 'https://htmlcolorcodes.com/assets/images/colors/neon-orange-color-solid-background-1920x1080.png', completed: false },
        { id: 1, name: 'Новинки', url: 'https://htmlcolorcodes.com/assets/images/colors/canary-yellow-color-solid-background-1920x1080.png', completed: false }
      ],
      hits: [
        { id: 0, name: 'one' },
        { id: 1, name: 'one' },
        { id: 2, name: 'one' },
        { id: 3, name: 'one' },
        { id: 4, name: 'one' }
      ]
    }
  },
  mounted () {
    this.startMethod()
  },

  methods: {
    startMethod () {
      this.slideractiveu = true
      this.screenslide = this.novelty
    },
    currentShow (ig) {
      this.dete = this.items[ig].name
      if (ig === 0) {
        this.screenslide = this.novelty
        this.slideractiveu = true
        this.top = false
        this.shop = false
        console.log(ig)
      }
      if (ig === 1) {
        this.screenslide = this.bonus
        this.slideractiveu = true
        this.top = false
        this.shop = false
        console.log(ig)
      }
      if (ig === 2) {
        this.slideractiveu = false
        this.top = true
        this.shop = false
        console.log(ig)
      }
      if (ig === 3) {
        this.slideractiveu = false
        this.top = false
        this.shop = true
        console.log(ig)
      }
    }
  }
}
</script>

<style>
  .vtb{
    margin-top: 25vh !important;
    left: 0;
  }
  .v-window__next{
   background: transparent !important;
  }
  .v-window__prev{
    background: transparent !important;
  }
  .buttonsoncar::before {
    background-color: transparent;
    opacity: 0 !important;
  }
  .iconleft{
    margin-left: 30vw;
    margin-top: 30vh;
  }
  .iconright{
    margin-right: 30vw;
    margin-top: 30vh;
  }
</style>

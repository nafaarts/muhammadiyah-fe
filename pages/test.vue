<template>
  <div>
    <button class="bg-green-500" @click="reload()">
      Reload Count
    </button>
    <br><br>
    Loading {{ count }} Squares<br>
    {{ squaresToFadeOut }} Squares left to fade out<br>
    <hr>

    <transition-group
      tag="ul"
      @before-enter="beforeEnter"
      @enter="enter"
      @leave="leave"
    >
      <li
        v-for="(i, index) in count"
        :key="i"
        class="square"
        stagger="50"
        :data-index="index"
      />
    </transition-group>
  </div>
</template>

<script>
import gsap from 'gsap'
export default {
  name: 'Body',
  data () {
    return {
      squaresToFadeOut: 0,
      count: 0
    }
  },
  methods: {
    reload () {
      this.count = Math.floor(Math.random() * 30)
      this.squaresToFadeOut = this.count
    },
    beforeEnter (el) {
      el.style.opacity = 0
      el.style.transform = 'translateY(50px)'
      el.style.transition = '.3s'
    },
    enter (el, done) {
      let i = 0
      gsap.to(el, {
        opacity: 1,
        y: 0,
        duration: 0.2,
        onComplete: () => {
          i++
        },
        delay: (el.dataset.index > 0 ? i : el.dataset.index) * 0.1
      })
    },
    leave (el) {
      gsap.to(el, {
        opacity: 0,
        y: '50px'
      })
    }
  },
  ready () {
    this.reload()
  }
}
</script>

<style>
.square {
  display: inline-block;
  width: 30px;
  height: 30px;
  margin: 4px;
  background-color: #666;
}
</style>

<template id="color-picker-template">
  <div class="color-picker">
    <div v-if="isVisible" class="color-picker__overlay" @click="hide"></div>
    <transition name="pop">
      <div v-if="isVisible" class="color-picker__flyout">
        <div class="color-chip" :style="{ background: color }">
          <div class="color-chip__inner">
            <h1 class="color-chip__title">HSL</h1>
            <h3 class="color-chip__subtitle">{{ colorString }}</h3>
          </div>
        </div>
        <div class="color-picker__inner">
          <div class="control" :style="gradientH">
            <input v-model="h" type="range" min="0" max="360" />
          </div>
          <div class="control" :style="gradientS">
            <input v-model="s" type="range" min="0" max="100" />
          </div>
          <div class="control" :style="gradientL">
            <input v-model="l" type="range" min="0" max="100" />
          </div>
        </div>
      </div>
    </transition>
    <div class="swatch" :style="{ background: color }" @click="toggle"></div>
  </div>
</template>

<script>
export default {
  name: 'ColorPicker',
  props: ['change', 'initial'],
  data() {
    return {
      isVisible: true,
      h: 265,
      s: 80,
      l: 99
    }
  },
  computed: {
    color() {
      const hsl = hsb2hsl(
        parseFloat(this.h) / 360,
        parseFloat(this.s) / 100,
        parseFloat(this.l) / 100
      )

      const c = hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%'

      const s = 'hsl(' + c + ')'
      this.change({
        color: s
      })
      return s
    },
    colorString() {
      const c = this.h + ', ' + this.s + '%, ' + this.l + '%'
      return c
    },
    gradientH() {
      const stops = []
      for (let i = 0; i < 7; i++) {
        const h = i * 60

        const hsl = hsb2hsl(
          parseFloat(h / 360),
          parseFloat(this.s) / 100,
          parseFloat(this.l / 100)
        )

        const c = hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%'
        stops.push('hsl(' + c + ')')
      }

      return {
        backgroundImage: 'linear-gradient(to right, ' + stops.join(', ') + ')'
      }
    },
    gradientS() {
      const stops = []
      let c
      let hsl = hsb2hsl(parseFloat(this.h / 360), 0, parseFloat(this.l / 100))
      c = hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%'
      stops.push('hsl(' + c + ')')

      hsl = hsb2hsl(parseFloat(this.h / 360), 1, parseFloat(this.l / 100))
      c = hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%'
      stops.push('hsl(' + c + ')')

      return {
        backgroundImage: 'linear-gradient(to right, ' + stops.join(', ') + ')'
      }
    },

    gradientL() {
      const stops = []
      let c

      let hsl = hsb2hsl(parseFloat(this.h / 360), 0, 0)
      c = hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%'
      stops.push('hsl(' + c + ')')

      hsl = hsb2hsl(parseFloat(this.h / 360), parseFloat(this.s / 100), 1)

      c = hsl.h + ', ' + hsl.s + '%, ' + hsl.l + '%'
      stops.push('hsl(' + c + ')')

      return {
        backgroundImage: 'linear-gradient(to right, ' + stops.join(', ') + ')'
      }
    }
  },

  mounted() {
    this.h = parseInt(Math.random() * 360)
  },
  methods: {
    show() {
      this.isVisible = true
    },
    hide() {
      this.isVisible = false
    },
    toggle() {
      this.isVisible = !this.isVisible
    }
  }
}

function hsb2hsl(h, s, b) {
  const hsl = {
    h
  }
  hsl.l = (2 - s) * b
  hsl.s = s * b

  if (hsl.l <= 1 && hsl.l > 0) {
    hsl.s /= hsl.l
  } else {
    hsl.s /= 2 - hsl.l
  }

  hsl.l /= 2

  if (hsl.s > 1) {
    hsl.s = 1
  }

  if (!hsl.s > 0) hsl.s = 0

  hsl.h *= 360
  hsl.s *= 100
  hsl.l *= 100

  return hsl
}
</script>

<style lang="scss" scoped>
.color-picker {
  position: relative;
}

.color-picker__overlay {
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0px;
  left: 0;
  background: black;
  z-index: 0;
  opacity: 0;
}

.color-picker__flyout {
  width: 240px;
  border: 1px solid #eee;
  border-radius: 4px;
  background: white;
  box-shadow: 0px 3px 7px rgba(0, 0, 0, 0.12);
  font-family: 'Roboto', 'Helvetica Neue', sans-serif;
  position: absolute;
  bottom: -170px;
  left: -100px;
  z-index: 2;
}

.color-picker__inner {
  padding: 1.5rem 1rem;
}

.color-chip {
  height: 260px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  border-radius: 4px 4px 0 0;
}

.color-chip__inner {
  text-align: center;
}

.color-chip__subtitle {
  margin-top: 0.5rem;
  opacity: 0.7;
  font-weight: normal;
  font-size: 15px;
  text-shadow: 0px 1px 2px rgba(0, 0, 0, 0.5);
}

.color-chip__title {
  color: white;
  margin: 0;
  font-size: 50px;
  letter-spacing: 4px;
  font-family: Helvetica Neue;
  text-shadow: 0px 1px 2px rgba(0, 0, 0, 0.5);
}

.control {
  width: 100%;
  height: 12px;
  border-radius: 12px;
  border: 1px solid #ddd;
}

.control + .control {
  margin-top: 1rem;
}

.control input {
  width: 100%;
  margin: 0;
}

.control input[type='range'] {
  -webkit-appearance: none;
  width: 100%;
  background: transparent;
}

.control input[type='range']:focus {
  outline: none;
}

.control input[type='range']::-ms-track {
  width: 100%;
  cursor: pointer;
  background: transparent;
  border-color: transparent;
  color: transparent;
}

.control input[type='range']::-webkit-slider-thumb {
  -webkit-appearance: none;
  border: 1px solid #ddd;
  height: 20px;
  width: 20px;
  border-radius: 50px;
  background: #ffffff;
  cursor: pointer;
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.12);
  margin-top: -4px;
}

.swatch {
  width: 24px;
  height: 24px;
  margin: 1rem auto 0 auto;
  border: 4px solid white;
  box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.3);
  cursor: pointer;
}

.swatch:hover {
  border: 4px solid white;
  opacity: 0.8;
  box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.3);
}

.pop-enter-active,
.pop-leave-active {
  transition: transform 0.5s, opacity 0.5s;
  transition-timing-function: cubic-bezier(0.8, 0.3, 0.25, 1.75);
  transform: scale(1);
}

.pop-enter,
.pop-leave-active {
  opacity: 0;
  transform: scale(0);
}
</style>

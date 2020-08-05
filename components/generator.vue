<template>
  <div class="mx-auto">
    <div class="grid grid-cols-10 md:mx-6 md:gap-5 mt-6 md:mt-16">
      <span class="text-center text-sm leading-5 text-gray-500">
        50
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        100
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        200
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        300
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        400
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        500
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        600
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        700
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        800
      </span>
      <span class="text-center text-sm leading-5 text-gray-500">
        900
      </span>

      <div
        v-for="(color, index) in colorArray"
        :key="index"
        class="md:rounded overflow-hidden"
      >
        <div
          class="h-16 md:h-24 md:rounded bg-gray-500"
          :style="{ backgroundColor: color }"
        ></div>
        <span
          class="hidden md:block text-sm w-full text-center text-gray-500"
          >{{ color }}</span
        >
      </div>
    </div>

    <div class="mt-6 md:mt-16 px-6">
      <div class="md:grid grid-cols-2 gap-8 mt-8">
        <div>
          <label
            for="maincolor"
            class="block text-sm font-medium leading-5 text-gray-700"
            >Main color</label
          >
          <div class="mt-1 relative rounded-md shadow-sm">
            <input
              id="maincolor"
              v-model="mainColor"
              class="form-input block w-full sm:text-sm sm:leading-5"
            />
          </div>
        </div>

        <div>
          <label
            for="location"
            class="block text-sm leading-5 font-medium text-gray-700"
            >Main color placement</label
          >
          <select
            id="location"
            v-model="mainColorPlacement"
            class="mt-1 form-select block w-full pl-3 pr-10 py-2 text-base leading-6 border-gray-300 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5"
          >
            <option
              v-for="(option, index) in placementOptions"
              :key="index"
              :value="option.value"
            >
              {{ option.text }}
            </option>
          </select>
        </div>
        <div>
          <label
            for="maincolor"
            class="block text-sm font-medium leading-5 text-gray-700"
          >
            Lighten
            <span
              class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium leading-4 bg-gray-100 text-gray-800"
              >{{ lightness }}</span
            >
          </label>
          <input
            id="myRange"
            v-model="lightness"
            type="range"
            min="0"
            max="100"
            value="50"
            step=".1"
            class="slider w-full"
          />

          <label
            for="maincolor"
            class="block text-sm font-medium leading-5 text-gray-700"
          >
            Light hue shift
            <span
              class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium leading-4 bg-gray-100 text-gray-800"
              >{{ lightHue }}</span
            >
          </label>
          <input
            id="myRange"
            v-model="lightHue"
            type="range"
            min="-120"
            max="120"
            value="50"
            step=".1"
            class="slider w-full"
          />

          <label
            for="maincolor"
            class="block text-sm font-medium leading-5 text-gray-700"
          >
            Light Desaturation
            <span
              class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium leading-4 bg-gray-100 text-gray-800"
              >{{ lightSat }}</span
            >
          </label>
          <input
            id="myRange"
            v-model="lightSat"
            type="range"
            min="0"
            max="100"
            value="50"
            step=".1"
            class="slider w-full"
          />
        </div>
        <div>
          <label
            for="maincolor"
            class="block text-sm font-medium leading-5 text-gray-700"
          >
            Darken
            <span
              class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium leading-4 bg-gray-100 text-gray-800"
              >{{ darkness }}</span
            >
          </label>
          <input
            id="myRange"
            v-model="darkness"
            type="range"
            min="0"
            max="100"
            value="50"
            step=".1"
            class="slider w-full"
          />

          <label
            for="maincolor"
            class="block text-sm font-medium leading-5 text-gray-700"
          >
            Dark hue shift
            <span
              class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium leading-4 bg-gray-100 text-gray-800"
              >{{ darkHue }}</span
            >
          </label>
          <input
            id="myRange"
            v-model="darkHue"
            type="range"
            min="-120"
            max="120"
            value="50"
            step=".1"
            class="slider w-full"
          />

          <label
            for="maincolor"
            class="block text-sm font-medium leading-5 text-gray-700"
          >
            Dark Desaturation
            <span
              class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium leading-4 bg-gray-100 text-gray-800"
              >{{ darkSat }}</span
            >
          </label>
          <input
            id="myRange"
            v-model="darkSat"
            type="range"
            min="0"
            max="100"
            value="50"
            step=".1"
            class="slider w-full"
          />
        </div>
      </div>
    </div>

    <div class="my-6 px-6 md:my-16 max-w-xl mx-auto">
      <div>
        <label
          for="email"
          class="block text-sm font-medium leading-5 text-gray-700"
          >Palette name</label
        >
        <div class="mt-1 relative rounded-md shadow-sm">
          <input
            id="email"
            v-model="paletteName"
            class="form-input block w-full sm:text-sm sm:leading-5"
          />
        </div>
      </div>

      <pre class="bg-gray-800 p-8 mt-6 rounded shadow-inner text-white">{{
        codeSnippet
      }}</pre>
    </div>
  </div>
</template>

<script>
const tinycolor = require('tinycolor2')
const slugify = require('slugify')
export default {
  name: 'Generator',
  data() {
    return {
      lightness: '45',
      lightHue: 0,
      lightSat: 0,
      darkness: '35',
      darkHue: 0,
      darkSat: 0,
      mainColorPlacement: 5,
      defaultMainColor: '#8034D5',
      paletteName: 'Brand',
      placementOptions: [
        { text: '100', value: 1 },
        { text: '200', value: 2 },
        { text: '300', value: 3 },
        { text: '400', value: 4 },
        { text: '500', value: 5 },
        { text: '600', value: 6 },
        { text: '700', value: 7 },
        { text: '800', value: 8 }
      ]
    }
  },
  computed: {
    mainColor: {
      get() {
        return this.defaultMainColor
      },
      set(val) {
        this.defaultMainColor = val
      }
    },
    colorArray() {
      let colors = []
      const mainColor = tinycolor(this.defaultMainColor).toRgbString()
      const darkSteps = 10 - this.mainColorPlacement
      const lightSteps = this.mainColorPlacement + 1

      const color50 = tinycolor(this.defaultMainColor)
        // .spin(parseInt(this.lightHue))
        // .desaturate(parseInt(this.lightSat))
        .lighten(this.lightness)
        .toRgbString()
      const color900 = tinycolor(this.defaultMainColor)
        // .spin(parseInt(this.darkHue))
        // .desaturate(parseInt(this.darkSat))
        .darken(this.darkness)
        .toRgbString()

      let lightColors = interpolateColors(color50, mainColor, lightSteps)

      lightColors.pop()

      // Desaturate and shift hue of light colors
      lightColors = lightColors.reverse()

      for (const [index, value] of lightColors.entries()) {
        const desatAmount = (parseInt(this.lightSat) / lightSteps) * index
        const hueShiftAmount = (parseInt(this.lightHue) / lightSteps) * index

        const editedColor = tinycolor(value)
          .desaturate(desatAmount)
          .spin(parseInt(hueShiftAmount))
          .toString()

        lightColors[index] = editedColor
      }

      lightColors = lightColors.reverse()

      const darkColors = interpolateColors(mainColor, color900, darkSteps)

      // Desaturate and shift hue of dark colors

      for (const [index, value] of darkColors.entries()) {
        const desatAmount = (parseInt(this.darkSat) / darkSteps) * index
        const hueShiftAmount = (parseInt(this.darkHue) / darkSteps) * index

        const editedColor = tinycolor(value)
          .desaturate(desatAmount)
          .spin(parseInt(hueShiftAmount))
          .toString()

        darkColors[index] = editedColor
      }

      colors = lightColors.concat(darkColors)

      return colors
    },
    codeSnippet() {
      const snippet = `// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        ${this.sanitizedPaletteName}: {
          '50': '${this.colorArray[0]}',
          '100': '${this.colorArray[1]}',
          '200': '${this.colorArray[2]}',
          '300': '${this.colorArray[3]}',
          '400': '${this.colorArray[4]}',
          '500': '${this.colorArray[5]}',
          '600': '${this.colorArray[6]}',
          '700': '${this.colorArray[7]}',
          '800': '${this.colorArray[8]}',
          '900': '${this.colorArray[9]}',
        }
      }
    }
  }
}`
      return snippet
    },
    sanitizedPaletteName() {
      return slugify(this.paletteName, {
        lower: true
      })
    }
  }
}
// Returns a single rgb color interpolation between given rgb color
// based on the factor given; via https://codepen.io/njmcode/pen/axoyD?editors=0010
function interpolateColor(color1, color2, factor) {
  if (arguments.length < 3) {
    factor = 0.5
  }
  const result = color1.slice()
  for (let i = 0; i < 3; i++) {
    result[i] = Math.round(result[i] + factor * (color2[i] - color1[i]))
  }

  const resultString = tinycolor(
    `rgb(${result[0]},${result[1]},${result[2]})`
  ).toHexString()
  return resultString
}
// My function to interpolate between two colors completely, returning an array
function interpolateColors(color1, color2, steps) {
  const stepFactor = 1 / (steps - 1)
  const interpolatedColorArray = []

  color1 = color1.match(/\d+/g).map(Number)
  color2 = color2.match(/\d+/g).map(Number)

  for (let i = 0; i < steps; i++) {
    interpolatedColorArray.push(
      interpolateColor(color1, color2, stepFactor * i)
    )
  }

  return interpolatedColorArray
}
</script>

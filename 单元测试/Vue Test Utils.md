# Vue Test Utils

> [Vue Test Utils](https://vue-test-utils.vuejs.org/zh/)



## example



```json
// package.json
{
  "scripts": {
    "test:unit": "jest"
  },
  "dependencies": {
    "vue": "^2.6.10",
  "devDependencies": {
    "@types/jest": "^24.0.23",
    "@vue/cli-plugin-unit-jest": "^4.0.5",
    "@vue/test-utils": "^1.0.0-beta.30",
    "babel-core": "^7.0.0-bridge.0",
    "jest": "^24.9.0",
    "ts-jest": "^24.2.0",
  },
  "jest": {
    "moduleNameMapper": {
      "^@/(.*)$": "<rootDir>/src/$1"
    },
    "moduleFileExtensions": [
      "js",
      "ts",
      "json",
      "vue"
    ],
    "transform": {
      ".*\\.(vue)$": "vue-jest",
      "^.+\\.tsx?$": "ts-jest",
      "^.+\\.js$": "<rootDir>/node_modules/babel-jest"
    },
    "testURL": "http://localhost/",
    "testRegex": "(/__tests__/.*|(\\.|/)(test|spec))\\.(jsx?|tsx?)$"
  }
}

```



```js
// jest.config.js
module.exports = {
  preset: "@vue/cli-plugin-unit-jest/presets/typescript-and-babel"
}

```

```js
// tests/utils/components/NavMenu.spec.ts
import jest from "jest"
import { shallowMount } from "@vue/test-utils"
import NavMenu from "@/components/NavMenu.vue"

var nav_data = [
	.......
]

describe("NavMenu.vue", () => {
  test("nav_itm click and emit update_selected_erea", async () => {
    var wrapper = shallowMount(NavMenu, {
      propsData: { nav_data }
    })
    const secondNavItem = wrapper.findAll(".nav_item:nth-of-type(2)").at(0)
    secondNavItem.trigger("click")
    // 很关键!
    await wrapper.vm.$nextTick()
    expect(wrapper.emitted()["update_selected_erea"][0]).toEqual([[1, 0, 0]])
  })
```


<template>
  <div class="layout-padding" style="max-width: 600px;">
    <div class="card" style="margin-top: 25px">
      <div class="card-title bg-primary text-center">
        <q-btn class="orange push" @click="show = !show">Toggle</q-btn>
      </div>
      <div class="card-content">
          <p class="caption">Enter CSS Class</p>
          <q-select filter v-model="enter" :options="enterSelectOptions"></q-select>
          <p class="caption">Leave CSS Class</p>
          <q-select filter v-model="leave" :options="leaveSelectOptions"></q-select>
      </div>
    </div>

    <div class="card" style="margin-top: 25px">
      <div class="card-title text-center">
        Single
      </div>
      <div class="card-content overflow-hidden">
        <q-transition
          appear
          :enter="enter"
          :leave="leave"
          :disable="disable"
        >
          <div v-if="show" v-html="loremipsum"></div>
        </q-transition>
      </div>
    </div>

    <div class="card" style="margin-top: 25px">
      <div class="card-title text-center">
        Group
      </div>
      <div class="card-content overflow-hidden">
        <q-transition
          group
          appear
          :enter="enter"
          :leave="leave"
          :disable="disable"
          class="group"
        >
          <div
            v-if="show"
            v-for="n in 3"
            :key="n"
            v-html="loremipsum"
          ></div>
        </q-transition>
      </div>
    </div>
  </div>
</template>

<script>
import { generalAnimations, inAnimations, outAnimations } from '../../../animations/animationList'

var enterSelectOptions = Array.from(generalAnimations).concat(inAnimations)
var leaveSelectOptions = Array.from(generalAnimations).concat(outAnimations)

// Since the animations are arrays of objects, we need to compare the label properties,
// in order to sort alphabetically on them
function alphabetically (a, b) {
  if (a.label < b.label) {
    return -1
  }
  if (a.label > b.label) {
    return 1
  }
  return 0
}

enterSelectOptions.sort(alphabetically)
leaveSelectOptions.sort(alphabetically)

export default {
  data () {
    return {
      enterSelectOptions,
      leaveSelectOptions,
      enter: 'bounceInLeft',
      leave: 'bounceOutRight',
      show: true,
      disable: false,
      loremipsum: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.'
    }
  }
}
</script>

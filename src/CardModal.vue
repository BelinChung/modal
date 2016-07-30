<template>
  <div :class="['modal', 'animated', visible ? 'is-active' : '']" :transition="transition" transition-mode="in-out">
    <div class="modal-background" @click="close"></div>
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">{{ title }}</p>
        <button class="delete" @click="close"></button>
      </header>
      <section class="modal-card-body">
        <partial v-if="partialBody" name="card-body"></partial>
        <slot></slot>
      </section>
      <footer class="modal-card-foot">
        <a class="button is-primary" @click="ok">{{ okText }}</a>
        <a class="button" @click="cancel">{{ cancelText }}</a>
      </footer>
    </div>
  </div>
</template>

<script>
import BaseModal from './BaseModal'

export default {
  mixins: [BaseModal],

  props: {
    partialBody: {
      type: Boolean,
      default: false
    },
    title: {
      type: String
    },
    okText: {
      type: String,
      default: 'Ok'
    },
    cancelText: {
      type: String,
      default: 'Cancel'
    }
  },

  methods: {
    ok () {
      this.close()
    },

    cancel () {
      this.close()
    }
  }
}
</script>

<style>
</style>

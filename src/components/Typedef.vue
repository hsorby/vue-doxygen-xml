<template>
  <dl :id="data.id" class="typedef">
    <dt class="typedef-name">
      {{ name }}
    </dt>
    <dt>
      <brief-description :data="briefDescription" />
      (<linked-text :item="linkedText" :class="'typedef-linked-text'" />)
    </dt>
    <dt class="typedef-definition">
      {{ processedDefinition }}
    </dt>
  </dl>
</template>

<script>
import { decodeHTML } from '../js/utilities'

import BriefDescription from './BriefDescription.vue'
import LinkedText from './LinkedText.vue'

export default {
  name: 'Typedef',
  components: { LinkedText, BriefDescription },
  props: {
    data: {
      type: Object
    }
  },
  computed: {
    processedDefinition() {
      return decodeHTML(this.data.definition)
    },
    name() {
      return this.data.name
    },
    briefDescription() {
      return { element: this.data.brief }
    },
    linkedText() {
      return this.data.typedefType
    }
  }
}
</script>

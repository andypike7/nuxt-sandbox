<template>
  <span>
    [
    <a :href="url">
      <slot>Default Link</slot>
    </a>
    <slot name="payload">Default Payload {{ url }}</slot>
    ]
  </span>
</template>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';
import { Prop } from 'vue-property-decorator';

@Component({})
export default class NavigationLink extends Vue {
  @Prop(String)
  url: string = '';
}
</script>

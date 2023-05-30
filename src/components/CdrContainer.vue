<!-- <script setup lang="ts">
defineProps<{ bar?: string }>();
</script>
<template>
  <div>{{ bar }}</div>
</template>
<style lang="scss" scoped>
.cdr-container {
  @include cdr-text-default;
  @include cdr-container-base;
}

.cdr-container--static {
  @include cdr-container-static;
}
</style> -->

<script lang="ts">
import { defineComponent, useCssModule, computed } from 'vue';
import propValidator from '../util/propValidator';
import mapClasses from '../util/mapClasses';

/** Provides base margins and responsive layout logic for pages */
export default defineComponent({
  name: 'CdrContainer',
  props: {
    /** Sets the HTML tag for the container element */
    tag: {
      type: String,
      default: 'div',
    },
    /**
     * Controls whether container is static or fluid width.
     * @demoSelectMultiple false
     * @values static, fluid
   */
    modifier: {
      type: String,
      default: 'static',
      validator: (value: string) => propValidator(
        value,
        ['static', 'fluid'],
        false,
      ),
    },
  },

  setup(props) {
    const baseClass = 'cdr-container';
    const modifierClass = computed(() => `${baseClass}--${props.modifier}`);

    return {
      style: useCssModule(),
      baseClass,
      modifierClass,
      mapClasses,
    };
  },
});

</script>

<template>
  <component
    :is="tag"
    :class="mapClasses(style, baseClass, modifierClass)"
  >
    <!-- @slot CdrContainer content  -->
    <slot />
  </component>
</template>

<style lang="scss">
.cdr-container {
  @include cdr-text-default;
  @include cdr-container-base;
}

.cdr-container--static {
  @include cdr-container-static;
}
</style>

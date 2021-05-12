<template>
  <div>
    <slot>
      default content
      <!-- this will only show if we donn't pass something in -->
    </slot>
    <div class="named-slots">
      <slot name="links"></slot>
    </div>
  </div>
</template>

<script></script>

<style></style>

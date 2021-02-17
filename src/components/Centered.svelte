<script>
  export let width = '100%';
</script>

<div style="--width: {width}" class="wrapper">
  <slot />
</div>

<style>
  @media screen and (min-width: 768px) {
    .wrapper {
      /* width: var(--width); doesnt't work in sapper? */
      max-width: 600px;
      margin: 0 auto;
    }
  }
  .wrapper{
    height: 100%;
  }
</style>

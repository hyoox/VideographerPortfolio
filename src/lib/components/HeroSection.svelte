<script lang="ts">
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";

  let visible = false;
  onMount(() => {
    visible = true;
  });
</script>

<section
  id="home"
  class="relative h-screen flex items-center justify-center overflow-hidden bg-[#0F1620]"
>
  <video
    autoplay
    loop
    muted
    class="absolute w-auto min-w-full min-h-full max-w-none opacity-30"
  >
    <source src="/hero-background.mp4" type="video/mp4" />
    Your browser does not support the video tag.
  </video>

  {#if visible}
    <div class="relative z-[1] text-center max-w-5xl mx-auto px-4">
      <h2
        in:fly={{ y: 20, duration: 500, delay: 200 }}
        class="text-6xl md:text-8xl font-display font-bold text-white mb-6"
      >
        Capturing Life's Moments
      </h2>
      <p
        in:fly={{ y: 20, duration: 500, delay: 400 }}
        class="text-xl md:text-2xl text-gray-200 mb-12 font-sans"
      >
        Professional Videography Services
      </p>
      <a
        href="#portfolio"
        in:fly={{ y: 20, duration: 500, delay: 600 }}
        class="inline-block bg-white hover:bg-gray-100 text-gray-900 font-sans font-medium px-8 py-3 rounded-full transition-colors duration-300"
      >
        View Portfolio
      </a>
    </div>
  {/if}
</section>

<style>
  .shadow-text {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }
</style>

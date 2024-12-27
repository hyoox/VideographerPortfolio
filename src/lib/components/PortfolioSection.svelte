<script lang="ts">
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";

  const videos = [
    { id: "897183399", title: "Chrysa Tsaltampasi - Gia Sena" },
    { id: "897183399", title: "Idra Kayne - Gia Sena" },
    { id: "897183399", title: "Nikola Leivaditi - Music Video" },
    { id: "897183399", title: "Village Cinemas Promo" },
    { id: "897183399", title: "Kryolan Beauty Campaign" },
    { id: "897183399", title: "+PSX Fashion Film" },
  ];

  let visible = false;
  onMount(() => {
    visible = true;
  });
</script>

<section id="portfolio" class="py-20 bg-gray-900">
  <div class="container mx-auto px-6">
    {#if visible}
      <h2
        in:fly={{ y: 20, duration: 500 }}
        class="text-4xl font-display font-bold text-center text-white mb-12"
      >
        Featured Work
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        {#each videos as video, index}
          <div
            in:fly={{ y: 50, duration: 500, delay: index * 100 }}
            class="bg-gray-800 rounded-lg shadow-lg overflow-hidden"
          >
            <div class="aspect-w-16 aspect-h-9">
              <iframe
                title={video.title}
                src={`https://player.vimeo.com/video/${video.id}?background=1&autoplay=1&loop=1&byline=0&title=0`}
                allow="autoplay; fullscreen; picture-in-picture"
                allowfullscreen
                class="w-full h-full"
              ></iframe>
            </div>
            <div class="p-4">
              <h3 class="text-xl font-display text-white">
                {video.title}
              </h3>
            </div>
          </div>
        {/each}
      </div>
      <div class="text-center mt-12">
        <a
          href="https://vimeo.com/itstonykris"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-block bg-blue-500 hover:bg-blue-600 text-white font-sans font-medium py-3 px-8 rounded-full transition duration-300"
        >
          View Full Portfolio on Vimeo
        </a>
      </div>
    {/if}
  </div>
</section>

<script lang="ts">
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";

  let visible = false;
  onMount(() => {
    visible = true;
  });
</script>

<section class="py-20 bg-gray-800">
  <div class="container mx-auto px-6">
    {#if visible}
      <h2
        in:fly={{ y: 20, duration: 500 }}
        class="text-4xl font-display font-bold text-center text-white mb-8"
      >
        About
      </h2>
      <div class="flex flex-col md:flex-row items-center justify-between">
        <div
          in:fly={{ x: -50, duration: 500, delay: 200 }}
          class="md:w-1/2 mb-8 md:mb-0"
        >
          <img
            src="/tonykris.jpeg"
            alt="Tony Kris"
            class="rounded-lg shadow-xl w-80 h-80 object-cover mx-auto"
          />
          <div class="text-center mt-4 font-sans">
            <p class="text-gray-300">📍 Athens, Greece</p>
            <p class="text-gray-300">he/him</p>
          </div>
        </div>
        <div
          in:fly={{ x: 50, duration: 500, delay: 400 }}
          class="md:w-1/2 md:pl-10"
        >
          <p class="text-gray-300 text-lg mb-6 leading-relaxed">
            Born in Athens in 1993, Tony Kris grew up in Nafplio and has been
            creating videos from a very young age. His professional filmmaking
            journey began under the mentorship of actor Thanasis Tsaltampasis,
            with whom he also created a short film.
          </p>
          <p class="text-gray-300 text-lg mb-6 leading-relaxed">
            He has collaborated with Athenian Theaters as a photographer and
            cinematographer, and has shot and filmed for Village Cinemas and
            Open TV. He has worked with beauty brand Kryolan, skincare company
            Caudalie, and fashion brand +PSX as a videographer.
          </p>
          <p class="text-gray-300 text-lg leading-relaxed">
            His lens has captured notable figures including Michalis
            Hatzigiannis, Giorgos Kapoutzidis, Aliki Alexandraki, Stelios
            Iakovidis, Maria Ekmektsoglou, and Aphrodite Gerokonstanti. He
            frequently creates music video clips for renowned artists such as
            Chrysa Tsaltampasi, Idra Kayne, and Nikola Leivaditi. His most
            recent work includes a series of photographic sessions with top
            model Vicky Koulianou.
          </p>
        </div>
      </div>
    {/if}
  </div>
</section>

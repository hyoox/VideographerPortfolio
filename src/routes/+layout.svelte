<script lang="ts">
  import "../app.css";
  import { Instagram } from "lucide-svelte";
  import VimeoIcon from "$lib/components/VimeoIcon.svelte";

  function scrollToTop(event: MouseEvent) {
    event.preventDefault();
    const element = document.getElementById("home");
    if (element) {
      element.scrollIntoView({ behavior: "smooth" });
    }
  }
</script>

<div class="min-h-screen bg-gray-900 transition-colors duration-300 font-sans">
  <header class="fixed w-full z-10 bg-gray-800 shadow-md">
    <nav class="container mx-auto px-6 py-3 flex justify-between items-center">
      <a
        href="#home"
        on:click={scrollToTop}
        class="text-3xl font-display font-bold text-white hover:text-gray-200 transition-colors duration-300"
      >
        Tony Kris
      </a>
    </nav>
  </header>

  <slot />

  <footer class="bg-gray-800 text-white py-6">
    <div class="container mx-auto px-6 text-center">
      <div class="flex justify-center space-x-8 mb-4">
        <a
          href="https://vimeo.com/itstonykris"
          target="_blank"
          rel="noopener noreferrer"
          class="text-gray-300 hover:text-white transition-colors duration-300"
          aria-label="Vimeo"
        >
          <VimeoIcon class="w-6 h-6" />
        </a>
        <a
          href="https://instagram.com/itstonykris"
          target="_blank"
          rel="noopener noreferrer"
          class="text-gray-300 hover:text-white transition-colors duration-300"
          aria-label="Instagram"
        >
          <Instagram size={24} />
        </a>
      </div>
      <p class="font-sans text-sm">
        &copy; 2024 Tony Kris. All rights reserved.
      </p>
    </div>
  </footer>
</div>

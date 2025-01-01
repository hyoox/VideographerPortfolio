<script lang="ts">
  import { fade, fly } from "svelte/transition";

  export let type: "success" | "error";
  export let message: string;
  export let show: boolean;
</script>

{#if show}
  <div
    in:fly={{ y: -20, duration: 300 }}
    out:fade={{ duration: 200 }}
    class="fixed top-24 left-1/2 transform -translate-x-1/2 z-50 px-6 py-3 rounded-lg shadow-lg {type ===
    'success'
      ? 'bg-green-500'
      : 'bg-red-500'}"
  >
    <p class="text-white font-medium">{message}</p>
  </div>
{/if}

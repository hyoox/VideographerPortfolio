<script lang="ts">
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";

  let visible = false;
  onMount(() => {
    visible = true;
  });

  function handleSubmit(event: SubmitEvent) {
    event.preventDefault();
    const form = event.target as HTMLFormElement;
    const email = form.email.value;
    const subject = form.subject.value;
    const message = form.message.value;

    window.location.href = `mailto:itstonykris@gmail.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(message)}`;
  }
</script>

<section class="py-20 bg-gray-800">
  <div class="container mx-auto px-6">
    {#if visible}
      <h2
        in:fly={{ y: 20, duration: 500 }}
        class="text-4xl font-display font-bold text-center text-white mb-8"
      >
        Contact
      </h2>
      <div class="max-w-3xl mx-auto text-center mb-12">
        <p class="text-gray-300 text-lg font-sans leading-relaxed">
          For collaborations, bookings, or inquiries, please send me a message.
        </p>
      </div>
      <form
        on:submit={handleSubmit}
        in:fly={{ y: 50, duration: 500, delay: 200 }}
        class="max-w-lg mx-auto font-sans"
      >
        <div class="mb-4">
          <label
            for="email"
            class="block text-gray-300 text-sm font-medium mb-2"
            >Your Email</label
          >
          <input
            type="email"
            id="email"
            name="email"
            class="shadow appearance-none border rounded w-full py-2 px-3 bg-gray-700 text-white leading-tight focus:outline-none focus:shadow-outline"
            required
          />
        </div>
        <div class="mb-4">
          <label
            for="subject"
            class="block text-gray-300 text-sm font-medium mb-2">Subject</label
          >
          <input
            type="text"
            id="subject"
            name="subject"
            class="shadow appearance-none border rounded w-full py-2 px-3 bg-gray-700 text-white leading-tight focus:outline-none focus:shadow-outline"
            required
          />
        </div>
        <div class="mb-6">
          <label
            for="message"
            class="block text-gray-300 text-sm font-medium mb-2">Message</label
          >
          <textarea
            id="message"
            name="message"
            rows={4}
            class="shadow appearance-none border rounded w-full py-2 px-3 bg-gray-700 text-white leading-tight focus:outline-none focus:shadow-outline"
            required
          ></textarea>
        </div>
        <div class="flex items-center justify-center">
          <button
            type="submit"
            class="bg-blue-500 hover:bg-blue-600 text-white font-medium py-2 px-6 rounded-full focus:outline-none focus:shadow-outline transition duration-300"
          >
            Send Message
          </button>
        </div>
      </form>
    {/if}
  </div>
</section>

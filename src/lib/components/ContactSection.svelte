<script lang="ts">
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";
  import emailjs from "@emailjs/browser";
  import Notification from "./Notification.svelte";

  let visible = false;
  let sending = false;
  let success = false;
  let error = false;
  let showNotification = false;

  onMount(() => {
    visible = true;
    emailjs.init("LgxdtZ-ivsAClHWF_");
  });

  async function handleSubmit(event: SubmitEvent) {
    event.preventDefault();
    sending = true;
    error = false;
    success = false;
    showNotification = false;

    try {
      const form = event.target as HTMLFormElement;
      const result = await emailjs.sendForm(
        "service_wzme1eu",
        "template_ucu4uri",
        form,
        "LgxdtZ-ivsAClHWF_"
      );

      if (result.text === "OK") {
        success = true;
        showNotification = true;
        form.reset();
        setTimeout(() => {
          showNotification = false;
        }, 5000); // Hide notification after 5 seconds
      } else {
        error = true;
        showNotification = true;
        setTimeout(() => {
          showNotification = false;
        }, 5000);
      }
    } catch (e) {
      error = true;
      showNotification = true;
      console.error(e);
      setTimeout(() => {
        showNotification = false;
      }, 5000);
    } finally {
      sending = false;
    }
  }
</script>

<Notification
  show={showNotification}
  type={success ? "success" : "error"}
  message={success
    ? "Message sent successfully!"
    : "Failed to send message. Please try again."}
/>

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
            name="from_email"
            class="shadow appearance-none border rounded w-full py-2 px-3 bg-gray-700 text-white leading-tight focus:outline-none focus:shadow-outline"
            required
          />
        </div>
        <div class="mb-4">
          <label for="name" class="block text-gray-300 text-sm font-medium mb-2"
            >Your Name</label
          >
          <input
            type="text"
            id="name"
            name="from_name"
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
        <input type="hidden" name="to_name" value="Tony" />
        <div class="flex flex-col items-center justify-center space-y-4">
          <button
            type="submit"
            disabled={sending}
            class="bg-blue-500 hover:bg-blue-600 disabled:bg-blue-400 text-white font-medium py-2 px-6 rounded-full focus:outline-none focus:shadow-outline transition duration-300"
          >
            {#if sending}
              Sending...
            {:else}
              Send Message
            {/if}
          </button>
        </div>
      </form>
    {/if}
  </div>
</section>

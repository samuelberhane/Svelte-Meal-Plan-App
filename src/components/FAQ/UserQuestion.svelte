<script>
  let email = "";
  let message = "";
  import { inview } from "svelte-inview";
  import { animateComponent } from "../../utils/functions/animation";
  import axios from "axios";
  import { baseBackendUrl } from "../../utils/routes/authRoutes";
  import { toast } from "@zerodevx/svelte-toast";
  import { errorClasses, successClasses } from "../../utils/toast/toastCustom";

  // send message from the user
  const handleSubmit = async () => {
    try {
      await axios.post(`${baseBackendUrl}/messages/`, {
        email,
        message,
      });
      email = "";
      message = "";
      toast.push("Message send successfully.", { theme: successClasses });
    } catch (error) {
      toast.push("Message can not be send.", { theme: errorClasses });
    }
  };
</script>

<!-- users' additional question form -->
<section class="bg-[#eae8e8cd] py-7">
  <div class="max-w-6xl mx-auto px-3">
    <h1
      use:inview
      on:inview_change={(e) => animateComponent(e, "fromLeft")}
      class="font-semibold font-[Roboto] text-3xl md:text-4xl relative left-0 xl:text-[30px] lg:text-2xl mb-3 text-[#a32389]"
    >
      Have a different question?
    </h1>
    <p class="font-[Alkatra]">
      At the core of our values is providing exceptional personalized assistance
      to each and every one of our clients. Should you require further
      clarification, feel free to peruse our extensive repository of knowledge
      at Plate Plan Knowledge Base. Alternatively, you may reach out to us
      through the messaging function below for a casual chat. Our team is
      available on weekdays from 9 to 5 Mountain time, and we are committed to
      responding to your queries within 12 hours, even if they are sent beyond
      our usual working hours.
    </p>

    <!-- form -->
    <form
      on:submit|preventDefault={handleSubmit}
      class="mt-4 font-[Alkatra] relative bottom-0"
      use:inview
      on:inview_change={(e) => animateComponent(e, "fromBottom")}
    >
      <input
        type="email"
        placeholder="Enter Your Email"
        bind:value={email}
        class="block mb-3 input"
      />
      <textarea
        rows="12"
        placeholder="Your Message..."
        class="w-full input"
        bind:value={message}
      />
      <div class="flex justify-center mt-4">
        <button
          type="submit"
          class="px-12 hover:scale-[1.03] font-[Roboto] py-2 text-xl bg-[#7db9db] rounded-lg text-white font-semibold"
          >Send Message</button
        >
      </div>
    </form>
  </div>
</section>

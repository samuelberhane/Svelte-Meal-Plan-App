<script>
  import {
    CreateAccount,
    FaqAccordion,
    Footer,
    UserQuestion,
  } from "../../components";
  import { inview } from "svelte-inview";
  import Layout from "../../components/Higher/Layout.svelte";
  import { animateComponent } from "../../utils/functions/animation";
</script>

<Layout>
  <section class="pt-[80px] lg:pt-[100px]">
    <div class="w-full relative">
      <!-- bg-image -->
      <img
        src="/media/recipeBg1.jpg"
        alt="faqImage"
        class="w-full object-cover"
      />

      <!-- frequently asked question content -->
      <div
        class="absolute top-[30vh] lg:top-[60vh] bg-white z-20 w-full min-h-screen"
      >
        <div class="max-w-6xl mx-auto px-3">
          <!-- faq -->
          <h1
            use:inview
            on:inview_change={(e) => animateComponent(e, "fromLeft")}
            class="font-semibold relative left-0 font-[Merriweather] mt-8 text-[#a32389] text-3xl lg:text-4xl xl:text-[42px]"
          >
            Frequently Asked Questions
          </h1>

          <!-- accordion -->
          <FaqAccordion />
        </div>

        <!-- users question form -->
        <UserQuestion />

        <!-- create account ad -->
        <CreateAccount />

        <!-- Footer -->
        <Footer />
      </div>
    </div>
  </section>
</Layout>

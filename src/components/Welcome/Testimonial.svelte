<script>
  import { Scroll } from "../";
  import { inview } from "svelte-inview";
  import { animateComponent } from "../../utils/functions/animation";
</script>

<section
  class="relative bg-[#eae8e8cd] 2xl:pb-[90px] pb-[700px] md:pb-[500px] lg:pb-[130px] xl:pb-0"
>
  <!-- Background image -->
  <img
    src="/media/testimonialBg.jpeg"
    alt="foodImage"
    class="w-full min-h-[500px] rounded-t-[100px]"
  />
  <div
    class="bg-[#eae8e8cd] absolute top-0 left-0 bottom-0 w-full rounded-t-[100px] pb-40"
  >
    <div class=" py-6">
      <h1
        use:inview
        on:inview_change={(e) => animateComponent(e, "fromLeft")}
        class="text-center text-[#a32389] text-3xl lg:text-4xl xl:text-[42px] relative left-0 font-semibold font-[Roboto] mb-4"
      >
        The benefits are lasting
      </h1>
      <!-- Benefits -->
      <div
        class="max-w-6xl mx-auto px-3 grid grid-cols-1 lg:grid-cols-2 gap-6 lg:gap-12 xl:gap-20"
      >
        <div class="bg-white px-8 py-12 relative left-0">
          <h1 class="font-bold text-xl font-[Roboto] lg:text-2xl mb-2">73%</h1>
          <h2 class="font-semibold font-[Merriweather] mb-2">
            Increase in consumption of “healthier foods”.
          </h2>
          <p class="font-[Alkatra] text-gray-500">
            “For me, healthier eating begins with meals I prepare myself, using
            fresh, healthy ingredients. Plan to Eat simplifies the process of
            locating and planning healthy recipes that my family will enjoy.”
          </p>
        </div>

        <div class="bg-white px-10 py-12 relative right-0">
          <h1 class="font-bold text-xl font-[Roboto] lg:text-2xl mb-2">73%</h1>
          <h2 class="font-semibold font-[Merriweather] mb-2">
            Increase in consumption of “healthier foods”.
          </h2>
          <p class="font-[Alkatra] text-gray-500">
            “For me, healthier eating begins with meals I prepare myself, using
            fresh, healthy ingredients. Plan to Eat simplifies the process of
            locating and planning healthy recipes that my family will enjoy.”
          </p>
        </div>
      </div>

      <!-- testimonial -->
      <Scroll />
    </div>
  </div>
</section>

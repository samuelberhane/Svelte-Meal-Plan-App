<script>
  import { inview } from "svelte-inview";
  import { animateComponent } from "../../utils/functions/animation";
</script>

<section class="recipeCurve min-h-[50vh]">
  <div class="max-w-6xl mx-auto px-3 mt-[100px]">
    <h1
      use:inview
      on:inview_change={(e) => animateComponent(e, "fromRight")}
      class="text-center relative right-0 font-bold text-3xl lg:text-4xl text-[#a32389] font-[Roboto] mb-3"
    >
      Plate Plan brings order to chaos.
    </h1>
    <div
      class="flex justify-center font-semibold text-sm font-[Merriweather] relative left-0"
    >
      <p class="max-w-[750px] text-[#3a3a3a]">
        Say goodbye to the chaos of meal planning! With our meal planning
        application, your scattered recipe bookmarks, kitchen notes, and grocery
        lists are consolidated into one reliable system. Our platform allows you
        to easily create and customize meal plans based on your preferences,
        dietary needs, and fitness goals. Say hello to stress-free meal planning
        and start enjoying healthy, delicious meals with ease!
      </p>
    </div>

    <div class=" mt-6">
      <div class="grid lg:grid-cols-2 gap-4">
        <!-- Recipe clipper -->
        <div class="relative">
          <img
            src="/media/recipeBg1.jpg"
            alt="bgImage"
            class="h-[340px] w-full"
          />
          <div
            class="absolute top-0 left-0 w-full bottom-0 bg-[#d3d3d3ea] p-4 flex items-center justify-center"
          >
            <div>
              <h1
                use:inview
                on:inview_change={(e) => animateComponent(e, "fromRight")}
                class="font-bold relative right-0 font-[Roboto] text-3xl mb-5"
              >
                Recipe Clipper
              </h1>
              <p class="font-[Alkatra] text-lg relative bottom-0">
                Our Recipe Clipper allows you to gather all your recipes
                together in your digital recipe book and organize them how you
                like.
              </p>
            </div>
          </div>
        </div>

        <!-- Planning Calender -->
        <div class="relative">
          <img
            src="/media/recipeBg2.jpg"
            alt="bgImage"
            class="h-[340px] w-full"
          />
          <div
            class="absolute top-0 left-0 w-full bottom-0 bg-[#d3d3d3ea] p-4 flex items-center justify-center"
          >
            <div>
              <h1
                class="font-bold font-[Roboto] text-3xl mb-5 relative right-0"
                use:inview
                on:inview_change={(e) => animateComponent(e, "fromRight")}
              >
                Planning Calendar
              </h1>
              <p class="font-[Alkatra] text-lg relative bottom-0">
                The meal planning calendar lets you plan ahead for any length of
                time, save meal plans to reuse in the future and add notes to
                remind yourself of the other events and obligations in your
                life.
              </p>
            </div>
          </div>
        </div>
      </div>

      <div class="relative mb-8 mt-4">
        <img
          src="/media/recipeBg3.jpg"
          alt="bgImage"
          class="h-[340px] w-full"
        />
        <div class="absolute top-0 left-0 w-full bottom-0 bg-[#d3d3d3ea] p-4">
          <h1
            class="font-bold font-[Roboto] text-3xl mb-5 mt-10 relative right-0"
            use:inview
            on:inview_change={(e) => animateComponent(e, "fromRight")}
          >
            Automated Shopping List
          </h1>
          <div
            class="font-[Alkatra] text-lg grid grid-cols-1 relative bottom-0cd xl:grid-cols-2 gap-20"
          >
            <p>
              But the very best part of Plan to Eat is the automated shopping
              list. When you add recipes to your calendar, the shopping list
              will automatically populate an organized list of ingredients you
              need to buy.
            </p>
            <p class="hidden xl:inline">
              You can add to and refine this list as much as you want, so you
              buy all the ingredients for your recipes, and any other household
              items you also need.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

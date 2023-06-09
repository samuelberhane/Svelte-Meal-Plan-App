<script>
  import { PrivateLayout, Title, NutrientsLineChart } from "../../components";
  import { DateInput } from "date-picker-svelte";
  import { onMount } from "svelte";
  import authStore from "../../stores/authStore";
  import { fetchUserMeals } from "../../utils/functions/fetchUserMeals";

  let userMeals = [];
  let loading = false;

  // fetch user's meal data
  onMount(() => {
    if ($authStore.token) {
      fetchUserMeals($authStore.userId, $authStore.token.access).then(
        (response) => {
          loading = response.loading;
          userMeals = response.userMeals;
        }
      );
    }
  });

  let labelName = "Calories";
  let startingDate = new Date(Date.now() - 3 * 24 * 60 * 60 * 1000);
  $: day = startingDate.getDate().toString().padStart(2, "0");
  $: month = (startingDate.getMonth() + 1).toString().padStart(2, "0");
  $: year = startingDate.getFullYear().toString().slice(-2);
  $: formattedDate = `${day}-${month}-${year}`;

  let days = [];

  // Create a reactive statement to watch for changes to the starting date and update the days array
  $: {
    days = [formattedDate.toString()]; // Clear the days array
    for (let i = 0; i < 6; i++) {
      let nextDay = new Date(startingDate);
      nextDay.setDate(startingDate.getDate() + i + 1); // Add i + 1 days to the starting date
      const day = nextDay.getDate().toString().padStart(2, "0");
      const month = (nextDay.getMonth() + 1).toString().padStart(2, "0");
      const year = nextDay.getFullYear().toString().slice(-2);
      const formattedDate = `${day}-${month}-${year}`;
      days.push(formattedDate.toString());
    }
  }

  // calories array
  let calories = [];
  $: {
    calories = [];
    // find the day in userMeals
    days.forEach((day) => {
      let findDay = userMeals.find(
        (meal) => meal.selectedDate.toString() == day
      );
      // if not meal created add 0
      if (!findDay) {
        calories.push(0);
      } else {
        // add the total calories for that day
        let currentDateCalories = 0;

        findDay.breakfast.forEach((data) => {
          currentDateCalories += data.calories / 3;
        });
        findDay.lunch.forEach((data) => {
          currentDateCalories += data.calories / 3;
        });
        findDay.snack.forEach((data) => {
          currentDateCalories += data.calories / 3;
        });
        findDay.dinner.forEach((data) => {
          currentDateCalories += data.calories / 3;
        });
        calories.push(currentDateCalories);
      }
    });
  }
</script>

<PrivateLayout>
  <div class="lg:ml-[250px]">
    <div class="px-4 md:px-12 py-4 lg:px-20">
      <!--title and starting day  -->
      <div class="flex flex-col md:flex-row justify-between mb-6">
        <Title title="Calories" subtitle="Chart of weekly calories intake" />
        <div>
          <!-- data picker  -->
          <h1 class="text-2xl xl:text-3xl mb-3 font-light font-[Merriweather]">
            Selected Start Date
          </h1>

          <!-- week start -->
          <div
            class="flex items-center gap-2 font-[Alkatra] text-sm font-light text-[#a3344a] mr-12"
          >
            <h1 class="text-lg">Starting Date:</h1>
            <DateInput bind:value={startingDate} />
          </div>
        </div>
      </div>

      <!-- calories chart -->
      <NutrientsLineChart {days} {labelName} data={calories} />
    </div>
  </div>
</PrivateLayout>

<script>
    import "../app.css";
    import DateInput from "../components/DateInput.svelte";
    import Arrow from "../assets/icons/arrow.svg";
    import AgeResult from "../components/AgeResult.svelte";

    const dateInputs = [
        { title: "DAY", placeholder: "DD" },
        { title: "MONTH", placeholder: "MM" },
        { title: "YEAR", placeholder: "YYYY" },
    ];
</script>

<div
    class="MainContainer bg-white mx-auto my-auto absolute left-2/4 top-2/4 w-6/12 h-fit"
    style="transform: translate(-50%,-50%); font-family : poppins; 	border-bottom-right-radius:250px"
>
    <div class="dates flex gap-8 m-7">
        {#each dateInputs as items, index}
            <DateInput title={items.title} placeholder={items.placeholder} />
        {/each}
    </div>

    <div class="flex flex-row items-center mr-6 ml-7">
        <hr class="w-full" style="background-color: #e7e7;" />
        <div style="background-color: #864CFF;" class="w-fit rounded-full p-5">
            <img src={Arrow} alt="arrow" />
        </div>
    </div>

    <div class="ageResult ml-7 mb-7">
        <AgeResult time="years"/>
        <AgeResult time="months"/>
        <AgeResult time="days"/>
    </div>
</div>

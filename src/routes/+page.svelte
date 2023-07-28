<script>
    import "../app.css";
    import DateInput from "../components/DateInput.svelte";
</script>

<div
    class="MainContainer bg-white mx-auto rounded-md my-auto absolute left-2/4 top-2/4 w-8/12 h-4/6"
    style="transform: translate(-50%,-50%); font-family : poppins"
>
    <div class="dates flex gap-20 m-7">
        <DateInput title="DAY" placeholder="DD" />
        <DateInput title="MONTH" placeholder="MM" />
        <DateInput title="YEAR" placeholder="YYYY" />
    </div>
</div>

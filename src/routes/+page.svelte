<script>
    import "../app.css";
    import DateInput from "../components/DateInput.svelte";
    import Arrow from '../../age-calculator-app-main/assets/images/arrow.svg'
</script>

<div
    class="MainContainer bg-white mx-auto my-auto absolute left-2/4 top-2/4 w-6/12 h-4/6"
    style="transform: translate(-50%,-50%); font-family : poppins; 	border-bottom-right-radius:250px"
>
    <div class="dates flex gap-8 m-7">
        <DateInput title="DAY" placeholder="DD" />
        <DateInput title="MONTH" placeholder="MM" />
        <DateInput title="YEAR" placeholder="YYYY" />
    </div>

    <img src={Arrow} alt="arrow"/>
</div>

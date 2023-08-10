<script>
    export let time;
    export let value;
</script>

<div class="flex items-center">
    <h1
        class="text-5xl xl:text-9xl font-bold italic mr-4"
        style="color: #864CFF; transform:translateY(10px)"
    >
        {$value || "--"}
    </h1>
    <h1 class="text-6xl sm:text-7xl xl:text-8xl font-extrabold italic">{time}</h1>
</div>

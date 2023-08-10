<script>
    export let time;
    export let value;
</script>

<div class="flex items-center">
    <h1
        class="text-9xl font-bold italic mr-4"
        style="color: #864CFF; transform:translateY(10px)"
    >
        {$value || "--"}
    </h1>
    <h1 class="text-8xl font-extrabold italic">{time}</h1>
</div>

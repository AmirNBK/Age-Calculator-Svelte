<script>
    export let title;
    export let placeholder;
    export let onChange;
    let inputValue = "";
</script>

<div>
    <h4 style="color : #8B8B8B" class="font-bold text-xs mb-2">{title}</h4>
    <input
        {placeholder}
        class="text-3xl w-36 h-16 rounded-md px-4 font-semibold outline-none"
        style="border: 1px solid #8B8B8B"
        bind:value={inputValue}
        on:input={() => onChange(inputValue, title)}
    />
</div>

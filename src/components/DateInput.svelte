<script>
    export let title;
    export let placeholder;
    export let onChange;
    let inputValue = "";
    export let empty;
    export let isValid;
</script>

<div>
    <h4
        style={`color : ${empty ? "#FC7C7C" : "#8B8B8B"}`}
        class="font-bold text-xs mb-2"
    >
        {title}
    </h4>
    <input
        {placeholder}
        class="text-xl lg:text-3xl w-24 sm:w-32 lg:w-36 h-12 sm:h-16 rounded-md px-4 font-semibold outline-none"
        style={`border: 1px solid ${empty ? "#FC7C7C" : "#8B8B8B"}`}
        bind:value={inputValue}
        on:input={() => onChange(inputValue, title)}
    />
    <p
        style="color: #FC7C7C;"
        class={`${!isValid ? "block text-sm mt-1 italic" : "hidden"}`}
    >
        Must be a valid {title}
    </p>
    <p
        style="color: #FC7C7C;"
        class={`${empty ? "block text-sm mt-1 italic" : "hidden"}`}
    >
        This field is required
    </p>
</div>

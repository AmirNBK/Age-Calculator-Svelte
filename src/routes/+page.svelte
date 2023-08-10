<script>
    import "../app.css";
    import DateInput from "../components/DateInput.svelte";
    import Arrow from "../assets/icons/arrow.svg";
    import AgeResult from "../components/AgeResult.svelte";
    import { useState } from "../hooks/hooks";

    const [birthDay, setBirthDay] = useState(0);
    const [birthMonth, setBirthMonth] = useState(0);
    const [birthYear, setBirthYear] = useState(0);
    const [ageYear, setAgeYear] = useState(0);
    const [ageMonth, setAgeMonth] = useState(0);
    const [ageDay, setAgeDay] = useState(0);
    const [isSelected, setIsSelected] = useState(false);
    const [allEmpty, setAllEmpty] = useState(false);

    const dateInputs = [
        { title: "DAY", placeholder: "DD", validity: true },
        { title: "MONTH", placeholder: "MM", validity: true },
        { title: "YEAR", placeholder: "YYYY", validity: true },
    ];

    const onChangeClick = (value, type) => {
        const numericValue = Number(value);
        if (type === "DAY") {
            setBirthDay(numericValue);
        } else if (type === "MONTH") {
            setBirthMonth(numericValue);
        } else {
            setBirthYear(numericValue);
        }
    };

    const onClick = () => {
        const birthDate = new Date($birthYear, $birthMonth - 1, $birthDay);
        const currentDate = new Date();
        let ageYears = currentDate.getFullYear() - birthDate.getFullYear();
        let ageMonths = currentDate.getMonth() - birthDate.getMonth();
        let ageDays = currentDate.getDate() - birthDate.getDate();
        if (!$birthDay && !$birthMonth && !$birthYear) {
            setAllEmpty(true);
        } else if (
            $birthDay > 31 ||
            $birthMonth > 12 ||
            $birthYear > currentDate.getFullYear() ||
            $birthDay === 0 ||
            $birthMonth === 0 ||
            $birthYear === 0
        ) {
            if ($birthDay > 31 || $birthDay === 0) {
                setAllEmpty(false);
                dateInputs[0].validity = false;
            }
            if ($birthMonth > 12) {
                setAllEmpty(false);
                dateInputs[1].validity = false;
            }
            if ($birthYear > currentDate.getFullYear()) {
                setAllEmpty(false);
                dateInputs[2].validity = false;
            }
        } else {
            setAllEmpty(false);
            dateInputs[0].validity = true;
            dateInputs[1].validity = true;
            dateInputs[2].validity = true;
            setIsSelected(true);

            if (ageDays < 0) {
                ageMonths--;
                const lastMonthDate = new Date(
                    currentDate.getFullYear(),
                    currentDate.getMonth(),
                    0
                );
                ageDays += lastMonthDate.getDate();
            }

            if (ageMonths < 0) {
                ageYears--;
                ageMonths += 12;
            }

            setAgeYear(ageYears);
            setAgeMonth(ageMonths);
            setAgeDay(ageDays);
        }
    };
</script>

<div
    class="MainContainer bg-white mx-auto my-auto absolute md:py-2 py-12 rounded-large left-2/4 top-2/4 w-fit rounded-br-120 sm:rounded-br-250 xl:w-6/12 h-fit"
    style="transform: translate(-50%,-50%); font-family : poppins;"
>
    <div class="dates flex gap-4 sm:gap-8 m-5 sm:m-7">
        {#each dateInputs as items, index}
            <DateInput
                title={items.title}
                placeholder={items.placeholder}
                onChange={onChangeClick}
                empty={$allEmpty}
                isValid={items.validity}
            />
        {/each}
    </div>

    <div class="flex flex-row items-center mr-6 ml-7">
        <hr class="w-full" style={`background-color: #e7e7`} />
        <div
            style={`background-color: ${$isSelected ? "#864CFF" : "#151515"}`}
            class="w-fit rounded-full p-4 md:p-5"
            role="button"
            on:click={() => onClick()}
            on:keydown={(event) => {
                if (event.key === "Enter") {
                    onClick();
                }
            }}
            tabindex="0"
        >
            <img src={Arrow} alt="arrow" class="w-8 md:w-fit" />
        </div>
    </div>

    <div class="ageResult ml-7 mb-7">
        <AgeResult time="years" value={ageYear} />
        <AgeResult time="months" value={ageMonth} />
        <AgeResult time="days" value={ageDay} />
    </div>
</div>

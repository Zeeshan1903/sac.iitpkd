<script>
    import { onMount } from "svelte";
    import "../../../app.css";
    import { writable } from "svelte/store";
    let section_buttons_text = [
        "Dashboard",
        "Clubs",
        "Announcements",
        // "Calendar",
        "Live-Events",
        // "Opportunities",
        // "Budget",
        "More",
    ];
    let selectedInd = writable(-2);
    onMount(() => {
        let selectedIndOption = localStorage.getItem("selectedInd");
        if (selectedIndOption != null) {
            selectedInd.set(parseInt(selectedIndOption));
        } else {
            selectedInd.set(0);
        }
    });
    /**
     * @param {number} index
     */
    function handleClick(index) {
        selectedInd.set(index);
        localStorage.setItem("selectedInd", JSON.stringify(index));
    }
    let hamOpened = writable(false);
    function hamburger() {
        hamOpened.set(!$hamOpened);
    }
</script>

<nav class="left-sidebar">
    <div
        class:section-buttons={$hamOpened}
        class:altSection-buttons={!$hamOpened}
    >
        <ul class="p-0">
            {#each section_buttons_text as section_button_text, index}
                <a
                    onclick={() => handleClick(index)}
                    href={index === 0
                        ? `/dashboard/`
                          : `/dashboard/${section_button_text.toLowerCase().replace("-", "_")}`}
                    class="text-black text-decoration-none web-link"
                >
                    <li
                        class="gap-3 d-flex align-items-center {$selectedInd ===
                            index - 1 || $selectedInd === index + 1
                            ? 'AllButtons adjacentButtons'
                            : 'AllButtons nonAdjacentButtons'} {$selectedInd ===
                        index
                            ? 'selectedButton'
                            : ''}"
                    >
                        <img
                            class="icons"
                            src="/{section_button_text}.svg"
                            alt="{section_button_text} icon"
                        />
                        <span class="button-text">{section_button_text}</span>
                    </li>
                </a>
            {/each}
        </ul>
    </div>
</nav>

<style>
    .left-logo {
        width: 200px;
    }

    .adjacentButtons {
        background: #ffcca0;
    }

    #img-logo {
        width: 75px;
        height: 76px;
    }

    #text-logo {
        width: 200px;
        height: 40px;
    }

    .nonAdjacentButtons {
        background-color: #ffe5d7;
    }

    .AllButtons {
        height: 60px;
        border-radius: 10px;
        display: flex;
        align-items: center;
        padding: 10%;
        margin-bottom: 10px;
        margin-left: 10px;
        /* justify-content: center; */
    }

    .selectedButton {
        background-color: #ff9941;
        font-weight: 600;
    }

    .icons {
        height: 20px;
        width: 20px;
    }

    .altSection-buttons {
        display: none;
        width: 200px;
    }

    .section-buttons {
        display: block;
        width: 200px;
    }

    @media screen and (min-width: 768px) {
        #ham {
            display: none;
        }

        .section-buttons,
        .altSection-buttons {
            display: block !important;
        }
    }

    @media screen and (max-width: 768px) {
        .section-buttons,
        .altSection-buttons {
            width: 100% !important;
        }
    }
</style>

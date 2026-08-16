<!-- The "Contents" sidebar on the longer pages: fixed alongside the text from xl up,
     stacked above it below that. Each entry names a `.section` in the page's markup by
     id, and bolds itself while that section is on screen. -->
<script lang="ts">
    type Section = {
        id: string;      // matches the id of the corresponding `.section` div
        label: string;
        note?: string;   // de-emphasised parenthetical, e.g. "as Instructor of Record"
    };

    let { sections }: { sections: Section[] } = $props();

    let onScreen = $state<Record<string, boolean>>({});

    $effect(() => {
        // A single threshold means one callback each way as a section crosses it.
        const observer = new IntersectionObserver(
            entries => {
                for (const entry of entries) {
                    onScreen[entry.target.id] = entry.intersectionRatio > 0.4;
                }
            },
            { threshold: 0.4 }
        );

        for (const { id } of sections) {
            const section = document.getElementById(id);
            if (section) observer.observe(section);
            else console.warn(`contents entry "${id}" matches no section`);
        }

        return () => observer.disconnect();
    });
</script>

<style>
    /* Hanging indent, so a wrapped entry lines up under its own first line rather
       than under the bullet. */
    li a {
        display: block;
        padding-left: 1em;
        text-indent: -1em;
    }

    .selected {
        font-weight: bold;
    }

    /* The sidebar is only 16rem wide, so a parenthetical left inline breaks in the
       middle of itself. Give it its own line; in the page headings it stays inline. */
    .subtitle {
        display: block;
        text-indent: 0;
    }
</style>

<div class="w-full xl:w-64 p-5 my-5 border rounded-xl border-gray-600 xl:fixed
    bg-white dark:bg-gray-800
    text-gray-500 dark:text-gray-300
    ">
    <h2 class="text-xl font-bold mb-4
        text-gray-700 dark:text-gray-400"
    >Contents</h2>
    <ul class="space-y-2 px-5">
        {#each sections as section (section.id)}
            <li>
                <!-- The space before the note is deliberately outside the tag: inside it,
                     Svelte trims it and the parenthetical runs into the label. -->
                <a href="#{section.id}" class="hover:font-bold" class:selected={onScreen[section.id]}>
                    {section.label}
                    {#if section.note}<span class="subtitle">({section.note})</span>{/if}
                </a>
            </li>
        {/each}
    </ul>
</div>

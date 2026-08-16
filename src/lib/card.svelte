<script lang="ts">
    import '@fortawesome/fontawesome-free/css/all.min.css'

    // Naming the props means a typo at a call site is a build error rather than a
    // quietly missing line; `title` and `text` are the only required ones.
    let {
        title,
        text,
        publisher = '',        // journal or magazine, shown before the title
        date = '',
        link = '',             // the title points here when given
        pdf = '',              // adds a PDF icon linking to the file
        audio = false,         // adds a speaker icon
        creativecommons = '',  // a Font Awesome licence glyph, e.g. fa-creative-commons-by
    }: {
        title: string;
        text: string;
        publisher?: string;
        date?: string;
        link?: string;
        pdf?: string;
        audio?: boolean;
        creativecommons?: string;
    } = $props();
</script>

<div class="container text-xl p-2 rounded-r-xl mb-5
    bg-gray-100 dark:bg-gray-950
    ">
    <a class="text-3xl p-1" href={link}>
        {#if publisher}
            <span class="text-gray-400 italic pr-2"> {publisher}: </span>
        {/if}
        <span class="text-gray-600"> {title} </span>
    </a>
    <p class="pt-1 text-gray-500">
        {#if date}
            <span class="text-gray-400 pr-2"> {date} </span>
        {/if}
        {#if audio}
            <i class="fa-solid fa-volume-low"></i>
        {/if}
        {#if pdf}
            <a href={pdf} aria-label="pdf"><i class="fa-solid fa-file-pdf"></i></a>
        {/if}
        {#if creativecommons}
            <i class="fa-brands fa-creative-commons"></i>
            <i class="fa-brands {creativecommons}"></i>
        {/if}
        <span class="pl-2 "> {text} </span>
    </p>
</div>

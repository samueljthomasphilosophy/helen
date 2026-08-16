<script lang="ts">
    import { page } from '$app/state';
    import { base } from '$app/paths';
</script>

<div class="container mx-auto">
    <div class="w-full lg:w-2/3 lg:mx-auto text-gray-600 dark:text-gray-300">
        <div class="section">
            <h2> {page.status} — {page.error?.message ?? 'Something went wrong'} </h2>
            <p class="text-xl pb-1 dark:text-gray-200">
                That page isn't here. It may have moved, or the link may have a typo in it.
                Every page is in the menu above, or start again from the
                <a class="text-blue-700 hover:underline" href={`${base}/`}>home page</a>.
            </p>
        </div>
    </div>
</div>

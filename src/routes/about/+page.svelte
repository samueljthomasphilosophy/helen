<script lang="ts">
    import Contents from '$lib/contents.svelte'
    import photo from '../../assets/HelenE-480.webp'
</script>

<div class="container mx-auto flex flex-col xl:flex-row">

    <Contents sections={[{ id: 'about', label: 'About' }]} />

    <!-- Content -->
    <div class="w-full xl:w-auto xl:ml-72
        text-gray-600 dark:text-gray-300">
        <!-- ABOUT -->
        <div id="about" class="section">
            <h2> About Me </h2>
            <img class="mb-4" src={photo} alt="a transsexual shorty" />
            <p class="text-xl pb-1 dark:text-gray-200">
                I go by Helen around friends and Thomas around state apparatchiks, authority figures, and the like.

                I am a PhD student and Graduate TA at the
                <a class="text-blue-700 hover:underline" href="https://philosophy.arizona.edu/person/samuel-thomas"
                >University of Arizona</a>.
                </p> <p class="text-xl py-1">
                My present research interests revolve around applied political philosophy. Specifically, I am interested in what we should do to prevent or reverse democratic backsliding, what ethical limits there are on economic sanctions, and which types of political compromises are unjust. I have also written on the concept of ideology.

                Before coming to the University of Arizona, I graduated from Arizona State University with a B.A. in Philosophy and Italian in 2019 and an M.A. in Philosophy in 2021. My M.A. thesis dealt with legal epistemology, specifically how judges and juries should evaluate different types of evidence. However, my interests have shifted a fair bit over the last couple years. Aside from my academic commitments, I am part of the Editorial Board for the
                <a class="text-blue-700 hover:underline" href="https://ctwgwebsite.github.io"
                >Critical Theory Working Group</a>.
                </p> <p class="text-xl py-1">
            </p>
        </div>
    </div>
</div>

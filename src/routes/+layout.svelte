
<script>

    import { browser, building, dev, version } from "$app/environment";
    import { navigating } from "$app/stores";
    import Header from "./header.svelte";
    import Footer from "./footer.svelte";
    import "./styles.css"
    import Episodes from "./episodes.svelte";

    export let data;

    $: ({ all_episodes } = data)



    console.log(browser,building,dev,version)

    // browser  ->  boolean, if app is running in browser
    // building -> boolean, true , if currently building in production..
    // dev ->  boolean, if in development mode 
    // version -> config.kit.version.name


</script>


{#if !!$navigating}

<div class="loading">

    Loading...
</div>

{/if}


<Header />


<main>


  <div class="main">

    <slot />

  </div>
     

    <aside>

        <Episodes episodes={all_episodes} />

    </aside>
   

</main>


<Footer />


<style>

  

    main {
        display: grid;
        grid-template-columns: 1fr 300px;
    }


    aside {
        order:-1;
    }


    .loading{

        position: fixed;
        inset: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: blue;
        color:white;
    }


</style>



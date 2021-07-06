<script>
  import Nav from '/src/components/Nav.svelte'
  import Footer from '/src/components/Footer.svelte'
</script>

<main>
  <Nav/>
    <slot/>
  <Footer/>
</main>


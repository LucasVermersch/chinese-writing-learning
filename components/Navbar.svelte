<script>
  import { Navbar, NavBrand, NavLi, NavUl, NavHamburger} from 'flowbite-svelte'
</script>

<div class="relative px-8 nav-spacing">
  <Navbar
    navClass="px-2 sm:px-4 py-2.5 absolute w-full z-20 top-0 left-0 border-b"
    let:hidden
    let:toggle
  >
    <NavBrand href="/">
      <span class="self-center text-purple-800 whitespace-nowrap text-xl font-semibold dark:text-white">Chinese writing training</span>
    </NavBrand>
    <NavHamburger on:click={toggle} />
    <NavUl {hidden}>
      <NavLi href="/" active={true}></NavLi>
      
    </NavUl>
  </Navbar>

</div>

<style>
  .nav-spacing {
    padding-bottom: 4rem;
  }
</style>
<script>
	import { onMount } from "svelte";
	import ChineseCharacter from "../components/ChineseCharacter.svelte";
    import Navbar from "../components/Navbar.svelte";
    import caracterList from "../lib/caracters/caracterList";

    const getCharacter = ()  => {
        return caracterList[Math.floor(Math.random() * caracterList.length)];
    }
    let characterToGuess = '';
    const newCharacterToGuess = () => {
        characterToGuess = getCharacter();
    }
    onMount(() => {
        newCharacterToGuess()
    });
</script>

<Navbar  />
<div class="flex justify-center" >
    <ChineseCharacter  on:new-character={newCharacterToGuess} character={characterToGuess} />
</div>


<style>

</style>
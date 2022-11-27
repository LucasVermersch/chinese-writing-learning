<script>

	import { Card, Button} from 'flowbite-svelte';
    import HanziWriter  from 'hanzi-writer';
	import { afterUpdate, createEventDispatcher, tick } from 'svelte';
    import pinyin from 'pinyin';
    
    export let character;

    const dispatch = createEventDispatcher();
    let writer;
    const renderCaracter = async () => {
        await tick();
        if(writer== null){
            writer = HanziWriter.create('caracter', character, {
                width: 300,
                height: 300,
                padding: 5,
                showCharacter: true,
                showOutline: true,
                showHintAfterMisses: 3,
                delayBetweenStrokes: 500,
            });
        }else{
            writer.setCharacter(character);
        }
        
        writer.quiz();
    }
   
    
    afterUpdate(async () => {
        await renderCaracter();
    });
</script>

<div class="p-8">
	<Card>
        <div class="flex justify-center">
            <p class="text-xl text-purple-800 antialiased font-bold"> {pinyin(character)}</p>
        </div>
        <div id="caracter"></div>
        <div class="flex gap-2">
            <Button color="purple" on:click={() => dispatch('new-character')}> Nouveau caractère </Button>
            <Button outline color="purple" on:click={renderCaracter} > Recommencer ce caractère</Button>

        </div>
    </Card>
</div>
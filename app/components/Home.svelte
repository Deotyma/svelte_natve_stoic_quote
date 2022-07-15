<page class="page">
	<actionBar title="quote of the day" class="action-bar">
	</actionBar>
	<stackLayout class="home">
        <image  src = "~/images/img{imgNumber}.png"/>
        <textView text={quote} class="quote"/>
        <textView text={author} class="quote"/>
		<button text="Next quote" on:tap="{ onTap }" class="button" />
	</stackLayout>
</page>

<script>
	//import { alert } from '@nativescript/core/ui/dialogs'
    import { quotes } from '../quotes.js'
    
    let min = 1
    let max = 10
    let imgNumber
    let quote
    let author 

    function randomImage() {
	imgNumber = Math.floor(Math.random() * (max - min)) + min; 
    }

    function randomQuote(){
        let i = Math.floor(Math.random() * quotes.length)
        quote = quotes[i].quote
        author = quotes[i].author
        return quote, author
    }
    randomQuote()

    function randomItems(){
        randomImage();
        randomQuote();
    }

   $: imgNumber ? 1 : randomImage();


	const onTap = () => randomItems() ;
</script>

<style>
    .home{
        background-color: #3aff96;
    }
    .quote{
        color: blue;
        font-size: 20rem;
        font-weight: 600;
    }
</style>
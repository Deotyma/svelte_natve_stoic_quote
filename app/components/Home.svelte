<page class="page">
	<actionBar title="quote of the day" class="action-bar">
	</actionBar>
	<stackLayout class="home">
        <image class="img"  src = "~/images/img{imgNumber}.png"/>
        <textView text={quote} class="quote"/>
        <label class="info">
            <formattedString>
                <span text=" {author}" class="author"/>
            </formattedString>
        </label>
		<button text="Next quote" on:tap="{ onTap }" class="button" />
	</stackLayout>
</page>

<script>
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
        background: rgb(105,134,14);
        background: linear-gradient(90deg, rgba(105,134,14,1) 0%, rgba(121,161,91,1) 100%);
    }
    .quote{
        color: #24261c;
        text-align: center;
        font-size: 30rem;
        font-weight: 600;
        margin-top: 10px;
        margin-bottom: 10px;
    }
    .author{
        color: #24261c;
        text-align: center;
        font-size: 20rem;
        font-weight: 400;
        margin-top: 10px;
        margin-bottom: 10px;
    }
    .info{
        text-align: center;

    }
    .button{
        background: rgb(220,162,219);
        background: linear-gradient(90deg, rgba(220,162,219,1) 0%, rgba(75,83,174,1) 100%);
        color: #24261c;
        font-size: 20rem;
        border-radius: 0 20px
       
    }
    .img{
        border-radius: 0 50px;
        margin: 20px;
        border: solid 5px #24261c;
    }
</style>
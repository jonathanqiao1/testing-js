<script lang="ts">
    import "../../app.css"
    import d20 from "$lib/d20.jpg"
    let clicks: number[] = []
    let cps = 0
    function real_test() {
        clicks.push(Date.now())
    }
    setInterval(() => {
        clicks = clicks.filter(x => Date.now() - x <= 5000)
        if (clicks.length <= 1) {
            cps = clicks.length
        }
        else {
            cps = (clicks.length / (Date.now() - clicks[0]) * 1000)
        }
    }, 1)


</script>
<img src={d20} alt="haha you are blind"/>

<a href="http://localhost:5173" class="size-28"> To Lunar CPS </a>
<button on:click={real_test} class="bg-amber-500 p-3 rounded-xl m-3 h-[500px] w-1/2 ">CLick Me!</button>

<p class="text-5xl text-blue-400 font-black">CPS: {cps.toFixed(5)}</p>

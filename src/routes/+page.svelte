<script lang="ts">
    import "../app.css"
    let x = 0
    let y = 0
    let cps = 0
    let check_click = 0
    let time = 1
    let clicked = 0
    let clicks: number[] = []

    function add_one() {
        x = x + 1
    }

    function cps_test() {
        cps = x
        y = 0
        x = 0
    }
    function start_test() {
        if (x === 0) {
            y = 1
        }
        x = x + 1
        if (y > 0) {
            setTimeout(cps_test, 1000)
            y = 0
        }
    }
    function real_test() {
        clicks.push(Date.now())
    }
    setInterval(() => {
        let i = 0
        while (clicks[i] - Date.now() > 1000) {
                clicks.splice(i, 1)
        }
        cps = Math.round(clicks.length / (Date.now() - clicks[0]) * 1000)
    }, 1)


</script>

<button on:click={real_test} class="bg-amber-500 p-3 rounded-xl m-3 h-[500px] w-1/2 ">CLick Me!</button>

<p class="text-5xl text-blue-400 font-black">CPS: {cps}</p>

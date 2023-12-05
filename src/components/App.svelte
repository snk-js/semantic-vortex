<script lang="ts">
    import "$/fonts.css";
    import { expoIn } from "svelte/easing";

    function shrink(node, { duration }) {
        return {
            duration,
            css: (t) => {
                const eased = expoIn(t);

                return `
					transform: scale(${eased}) rotate(${eased * 1080}deg);
					color: hsl(
						${~~(t * 360)},
						${Math.min(100, 1000 - 1000 * t)}%,
						${Math.min(50, 500 - 500 * t)}%
					);`;
            },
        };
    }

    let text =
        "In the universe's quiet corners, where light whispers secrets to the void, there dwells a riddle, wrapped in the shadows of space – the enigma of black holes. This tale isn't just a charting of stars and their silent ballet; it's a deeper dive into the nature of reality itself, a narrative spun from the threads of the unseen.\nOnce, in the cradle of time, where the universe breathed its first, the story unfolded. Stars, like newborns in a cosmic nursery, ignited, painting their stories across the heavens. Galaxies, those grand architects, sketched spirals and ellipses in the darkness. Among these celestial wonders, black holes emerged, nature's mysterious prodigies.\nBorn from the fiery demise of stars, these enigmatic entities cradle the echoes of cosmic catastrophes. Their gravity, relentless and unforgiving, weaves a fabric where even light cannot escape, where the usual rules of the cosmos falter and fall silent.\nIn their invisible embrace, these celestial giants serenade the universe. They don't just pull in matter; they tug at the very essence of wonder, holding secrets denser than their own cores. Here, in the heart of darkness, the universe's untold stories linger, waiting to be unraveled.\nBlack holes, silent and unseen, stand as paradoxical monuments. They are voids, yet brimming with untold narratives – the remnants of stars, the whispers of galaxies long gone, the silent echoes of the universe's past.\nThis tale, woven in the fabric of the unseen, is not just of celestial bodies but of the very nature of reality. It's a journey into the heart of darkness, where the greatest mysteries and truths of the cosmos dance together, forever intertwined in the silent poetry of the universe.\n";
</script>

<svelte:head>
    <link rel="stylesheet" href="" />
</svelte:head>

<div class="panel" in:shrink={{ duration: 5000 }}>
    {text}
</div>

<style>
    :global(body) {
        font-family: "Josefin Slab";
        font-style: italic;
        font-size: 2rem;
        margin: 0;
        background: radial-gradient(circle, rgba(13, 19, 32, 1) 0%, rgb(16, 24, 43) 100%);
    }
    .panel {
        color: antiquewhite;
        background: rgb(0, 0, 0, 0.5);
        width: 100%;
        height: 100vh;
        word-wrap: break-word;
        word-break: break-all;
    }
</style>

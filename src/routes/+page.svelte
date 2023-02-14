<script lang="ts">
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';

	let ready = false;
	let title = 'hewwo!';
	onMount(() => (ready = true));

	function typewriter(node: object, { speed = 1.5 }) {
		const text = node.childNodes[0].textContent;
		const duration = text.length / (speed * 0.01);

		return {
			duration,
			tick: (t) => {
				const i = Math.trunc(text.length * t);
				node.childNodes[0].textContent = text.slice(0, i);
			}
		};
	}

	// 0 = unclicked, 1 = yes, 2 = no
	let my_girlfriend = 0;

	function firstYes() {
		my_girlfriend = 1;
		title = 'here we go!';
	}

	function firstNo() {
		my_girlfriend = 2;
		title = 'here we go!';
	}

	let my_fiancee = 0;

    function secondYes() {
        my_fiancee = 1;
        title = "it's Valentine's!";
    }

    function secondNo() {
        my_fiancee = 2;
        title = "it's Valentine's!";
    }

    let my_wife = 0;

    function thirdYes() {
        my_wife = 1;
        title = "i love you a lot.";
    }
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

{#if ready}
	<h1 transition:typewriter>
		hey, welcome to the page. are you peach?
		<span class="cursor" />
	</h1>
	<div class="buttons">
		<button on:click={firstYes} transition:fade={{ duration: 500, delay: 3000 }}> yes </button>
		<button on:click={firstNo} transition:fade={{ duration: 500, delay: 3000 }}> no </button>
	</div>
{/if}

{#if my_girlfriend == 1}
	<h1 transition:typewriter>
        oh, hi there! i've been waiting for your arrival. you do seem to remember what day it is today,
        don't you?
		<span class="cursor" />
	</h1>
	<div class="buttons">
		<button on:click={secondYes} transition:fade={{ duration: 500, delay: 7750 }}> yes, i do! </button>
		<button on:click={secondNo} transition:fade={{ duration: 500, delay: 7750 }}> no, i really don't. </button>
	</div>
{/if}

{#if my_girlfriend == 2}
	<h1 transition:typewriter>
		impossible, only peach knows this link, you must be peach. you remember what today is, right?
		<span class="cursor" />
    </h1>
    <div class="buttons">
        <button on:click={secondYes} transition:fade={{ duration: 500, delay: 5000 }}> yes. </button>
        <button on:click={secondNo} transition:fade={{ duration: 500, delay: 5000 }}> no, i don't. </button>
    </div>
{/if}

{#if my_fiancee == 1}
    <h1 transition:typewriter>
        you do? it's Valentine's today, right? and because it's Valentine's, i have a few things i really want to
        tell you. just between the two of us. please click the button below to see what i have to say.
		<span class="cursor" />
    </h1>
    <div class="buttons">
        <button on:click={thirdYes} transition:fade={{ duration: 500, delay: 10000 }}> please click me. </button>
    </div>
{/if}

{#if my_fiancee == 2}
    <h1 transition:typewriter>
        oh, in the case you don't remember, it's Valentine's today! i have some things to tell you for this special day!
        please click the button below.
		<span class="cursor" />
    </h1>
    <div class="buttons">
        <button on:click={thirdYes} transition:fade={{ duration: 500, delay: 10000 }}> please click me. </button>
    </div>
{/if}

{#if my_wife == 1}
    <p transition:typewriter>
        I love you a lot. I'll start it off with that. This will sound like everything I have recited throughout these times,
        but I truly, truly love you a lot. I really wanted to plan this into one of those CYOA, but I realized I'm really bad
        at doing these, and learning takes a good bit. Something will come on your birthday though, so be on the lookout for that!
        Anyway, time for me to get to the main points. I know I screwed up really hard today, by falling asleep and not being able
        to spend time with you, especially on this very special date. I'm really sorry. I really wanted to give you this as a
        Valentine's present, in some more "physical" form, I guess, like having a gift and a piece of paper with either this, or the
        link to it written on it. At least, I managed to finish it so you could see it.
		<span class="cursor" />
    </p>

    <p transition:typewriter>
        You're very important to me. Everyday I want to say that I love you more and more, to the point that merely saying it isn't
        enough for me. Everyday being in love with you is a learning experience for me, both good things and bad things. You teach me
        and give me more things than I could ever ask for. I'm truly thankful for everything, from the bottom of my heart. I love you
        a lot. To the mainest point, to make up for today. Are you free tomorrow, 15th of February, 2023? Do you want to go to the
        movies together? Reply in my DMs &lt;3
        <span class="cursor" />
    </p>

    <div>
        <a href="https://github.com/j1nxie/daisuki-desu/blob/main/src/routes/%2Bpage.svelte">Click here</a> to see a few secretly named variables!
    </div>
{/if}

<style lang="scss">
    * {
        font-family: 'Comic Sans MS', serif;
        text-align: center;
    }

    :global(body) {
        max-width: 800px;
        margin: 0 auto;
        background-color: #c3b1e1;
    }

    button {
        text-align: center;
        margin: 0 auto;
        border-radius: 12px;
        font-size: 24px;
        background-color: #ffdfd3;
        padding: 18px;
    }

    h1 {
        position: relative;
    }

    p {
        position: relative;
    }

    p > .cursor {
        height: 1rem;
    }

    .cursor {
        display: inline-block;
        position: absolute;
        bottom: 0;
        width: 8px;
        height: 2rem;
        background: blue;
        animation: blink 0.8s infinite;
        margin-left: 0.25rem;
    }

    @keyframes blink {
        0% {
            background: transparent;
        }

        60% {
            background: cyan;
        }

        to {
            background: cyan;
        }
    }
</style>

<script>
    import "js-dos/dist/js-dos";
    import "js-dos/dist/js-dos.css";
    import { onMount } from "svelte";

    let dosDiv;
    onMount(() => {
        // @ts-ignore
        Dos(dosDiv, {
            noSocialLinks: true
        }).run("./CP-distribution.jsdos");
    });

    let showWindow = true;
</script>



<div bind:this={dosDiv} class="dos-div"></div>

{#if showWindow}
<div class="window-container">
    <div class="window">
        <div class="window-header">
            <span class="window-title">Vernier Charged Particles MS-DOS Version</span>
            <button class="close-button" on:click={()=>{showWindow = false}}>Close &#x2715;</button>
            <h1>Program information and help</h1>
        </div>
        <div class="window-body">
            <h2>How to enable touch controls</h2>
            <p>To enable touch controls, press the arrow button at the far left of the screen. Then, click on the eye button and click the phone icon:</p>
            <p style="text-align: center;"><img style="display: inline-block;" src="images/mobilelayouthelp.png"></p>
            <h2>Touch controls help</h2>
            <p>Press the <span class="tag">&gt;</span> key to toggle between the menu control scheme and the simulation control scheme.</p>
            <p>To increase/decrease the magnetic field, use the <span class="tag">+</span> and <span class="tag">-</span> buttons on the left.</p>
            <p>To increase/decrease the electric field, use the <span class="tag">+</span> and <span class="tag">-</span> buttons on the right.</p>
            <p><span class="tag">&uparrow;</span> - Go up in the menu</p>
            <p><span class="tag">&downarrow;</span> - Go down in the menu</p>
            <p><span class="tag">&#9166;</span> - Select menu item/confirm</p>
            <p><span class="tag">ESC</span> - Cancel/go back to menu</p>
            <p><span class="tag">C</span> - Clear the particle's path</p>
            <p><span class="tag">V</span> - Change the initial velocity (keyboard is required to enter input, which can be enabled by pressing the note icon in the left menu)</p>

            <h2>About this program</h2>
            <p>
                Charged Particles MS-DOS version is a simulation software developed by Vernier Software in 1991
                to help physics students learn about the effects of electric fields on charged particles.</p>
            <p>
                It was developed for the MS-DOS operating system, which at the time, was widely used on personal computers.
                Nowadays, DOS programs must be run through emulation software such as DOSBox, which is an emulator for
                Windows, macOS, and Linux, or JS-DOS, which is an emulator for HTML5/JavaScript.
            </p>
            <p>
                I decided to make this web-hosted verison of Charged Particles MS-DOS version because it and its labs were
                still being used in my high school, and I wanted to be able to run it on devices such as iPads without requiring
                any apps to be downloaded or any setup to be required. It uses <a href="https://js-dos.com/">JS-DOS</a> to emulate the program.
            </p>
            <p>
                Interestingly, this specific program has never been backed up anywhere on the internet! I was able to find
                <a href="https://archive.org/details/VERNIER-_CHARGED_PARTICLES">an Apple II version on Archive.org,</a>
                but I believe this is the first time the MS-DOS version has been backed up anywhere.
            </p>
            <h2>Resources</h2>
            <p>A .zip file including the original executable given to me by my physics teacher and the PDF for this lab can be found <a href="/dos-app/Charged-Particles.zip">here</a>.</p>
        </div>
    </div>
</div>
{/if}

{#if !showWindow}
<button class="open-window" on:click={()=>{showWindow = true}}>Info & help</button>
{/if}

<style>
    .dos-div{
        height: calc(100%);
    }
    .window-container{
        background-color: rgba(0,0,0,0.5);
        display: flex;
        align-items: center;
        justify-content: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 100;
    }
    .window{
        background-color: white;
        max-width: 800px;
        max-height: 600px;
        width: calc(100% - 60px);
        height: calc(100% - 60px);
        display: block;
        overflow: hidden;
        border-radius: 10px;
    }

    .window-header{
        padding: 20px 20px 15px;
        background-color: rgba(0,0,0,0.05);
    }
    .window-body{
        padding: 20px 20px 20px 20px;
        overflow: hidden scroll;
        height: calc(100% - 110px);
    }
    .window h1{
        font-size: 2em;
        font-weight: bold;
    }

    .window h2{
        font-size: 1.2em;
        font-weight: bold;
        margin-bottom: 0.5em
    }
    
    .window-title{
        color: rgb(100,100,100)
    }
    
    .close-button{
        text-align: right;
        background-color: rgb(255,100,100);
        color: white;
        padding: 4px 10px ;
        border-radius: 20px;
        top: 10px;
        right: 10px;
        float: right;
    }
    .window p:not(:last-child){
        margin-bottom: 1em;
    }

    .open-window{
        position: fixed;
        left: 10px;
        bottom: 10px;
        width: 132px;
        height: 40px;
        background-color: dodgerblue;
        z-index: 120;
        border-radius: 20px;
        background-image: url("/dos-app/information-outline.svg");
        background-position: 4px center;
        background-size: 32px;
        background-repeat: no-repeat;
        color: white;
        padding-left: 24px;
        font-size: 14px;
    }
    .tag{
        padding-left: 5px;
        padding-right: 5px;
        border-radius: 0.5em;
        background-color: lightgray;
        font-weight: bold;
    }
    .window a{
        color: dodgerblue;
    }
    .window a:hover{
        text-decoration: underline;
    }
</style>


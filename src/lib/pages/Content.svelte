<script lang="ts">
	import Anchor from "$lib/components/Anchor.svelte";

 
  

  import {SLURS} from "$lib/pages/slurs.ts";
  let selectedOption: { options: string|any[]; };
  let selectedRandomOption: string;
  let loading = false;

  const handleRandomize = () => {
    loading = true;
    setTimeout(() => {
      loading = false;
      if (selectedOption) {
        selectedRandomOption =
          selectedOption.options[
            Math.floor(Math.random() * selectedOption.options.length)
          ];
      }
    }, 1000);
  };
  </script>
  
  
  <section>
	<Anchor id="content" />
	
  <div
	class="flex flex-col items-center justify-center bg-center bg-no-repeat bg-cover page lg:bg-fixed bg-slate-900 bg-blend-soft-dark dark:bg-blend-soft-light dark:bg-slate-900"
	id="bg"
  >
		<div class="page-wrapper">
			<h1 class="title">
			Choose a race
			  </h1>
			  

					<select
					bind:value={selectedOption}
					on:change={() => {
					  loading = false;
					  selectedRandomOption = "";
					}}	>
					<option value="">------</option>
					{#each SLURS as randomOption}
					  <option value={randomOption}>
								  <h2 class="text_shadows"> {randomOption.displayText}</h2>
					  </option>
					{/each}
				  </select>
			  
				  <button on:click={handleRandomize} disabled={!selectedOption || loading}>
					Roll!
				  </button>
				
				  <div class="selected-option">
					{#if selectedRandomOption && !loading}
					<div class="content">
					  <h2 class="text_shadows">	{selectedRandomOption}</h2>
					</div>	
					{/if}
					{#if loading === true}
					<div class="cube-wrap">
						<div class="cube">
						  <div class="face"><span class="dots">1</span></div>
						  <div class="face"><span class="dots">2</span></div>
						  <div class="face"><span class="dots">3</span></div>
						  <div class="face"><span class="dots">4</span></div>
						  <div class="face"><span class="dots">5</span></div>
						  <div class="face"><span class="dots">6</span></div>
						</div>
					  </div>
				  
					{/if}


		

	   </div>
	</div>

  </section>
  
  <style>
	#bg {
	  width: 100%;
	height: 100vh;
	color: #fff;
	background-image: url("/src/bricks.jpg");
	background-size: 120% 120%;
	position: relative;
	
	}
	* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
  }
  
  
  
  @keyframes change {
	0% {
	  background-position: 0 50%;
	}
	
	50% {
	  background-position: 100% 50%;
	}
	
	100% {
	  background-position: 0 50%;
	}
  }
   
	/* --------------------------  title css--------------------------*/
	@import url('https://fonts.googleapis.com/css?family=Codystar:300&display=swap');
  
  body {
	 display: flex;
	 justify-content: center;
	 align-items: center;
	 font-family: 'Codystar';
  }
  
  
  @-webkit-keyframes glow {
	   from {
		color: #fff;
	  text-shadow: 0 0 10px #00fff2, 0 0 20px #00fff2, 0 0 30px #00fff2, 0 0 40px #00fff2, 0 0 50px #00fff2, 0 0 60px #00fff2, 0 0 70px #00fff2, 0 0 90px #00fff2;
	}
	
	to {
	   color: gray;
	  text-shadow: 0 0 20px #00fff2, 0 0 30px #00fff2, 0 0 40px #00fff2, 0 0 50px #00fff2, 0 0 60px #00fff2, 0 0 70px #00fff2, 0 0 80px #00fff2, 0 1 90px #00fff2;
	}
  }


  /*----------------------------------------------- */
  @keyframes change {
  0% {
    background-position: 0 50%;
  }
  
  50% {
    background-position: 100% 50%;
  }
  
  100% {
    background-position: 0 50%;
  }
}
  /*---------- */
  .page-wrapper {
	
    text-align: center;
	color: #1F2937;
	
	border-radius:10px;
	
	
  }
  button {
    cursor: pointer;
    margin-left: 1rem;
    padding: 0.5rem 1rem;
    color: #1F2937;
    border-color: #558492;
    border-radius: 5px;
    font-weight: bold;
	background-color: #7ac2ec;
  }
  button:disabled {
    pointer-events: none;
	background-color: #2e70d3;
  }
  button:active {
    transform: scale(0.98);
	color:#08415c;
	background-color: #7ac8ec;
  }
  
  button:hover {
    background-color: #54a0df;
    border-color: #074183;
  }
  .selected-option {
    margin-top: 1.5rem;
    font-size: 1.5rem;
    color: #85f0b5;
    font-weight: 600;
	
  }

 
/* ---------------------------- chosen place animation css-----------------------------  */
 :root {
	 --color-primary: #a2dcf6;
	 --color-secondary: #90f1f4;
	 --color-tertiary: #3d73b1;
	 --color-quaternary: #6aa4f0;
	 --color-quinary: #0c2363;
}

 .content {
	 display: flex;
	 align-content: center;
	 justify-content: center;
}
.text_shadows {
  text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary),
    9px 9px var(--color-quaternary), 12px 12px 0 var(--color-quinary);
  font-family: bungee, sans-serif;
  font-weight: 200;
  text-transform: uppercase;
  font-size: calc(1.5rem + 3vw);
  text-align: center;
  margin: 0;
  color: var(--color-primary);
  
  animation: shadows 2.00s ease-in infinite, move 3.2s ease-in infinite;

  letter-spacing: 0.4rem;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
 @keyframes shadows {
	 0% {
		 text-shadow: none;
	}
	 10% {
		 text-shadow: 3px 3px 0 var(--color-secondary);
	}
	 20% {
		 text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary);
	}
	 30% {
		 text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary), 9px 9px var(--color-quaternary);
	}
	 40% {
		 text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary), 9px 9px var(--color-quaternary), 12px 12px 0 var(--color-quinary);
	}
	 50% {
		 text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary), 9px 9px var(--color-quaternary), 12px 12px 0 var(--color-quinary);
	}
	 60% {
		 text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary), 9px 9px var(--color-quaternary), 12px 12px 0 var(--color-quinary);
	}
	 70% {
		 text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary), 9px 9px var(--color-quaternary);
	}
	 80% {
		 text-shadow: 3px 3px 0 var(--color-secondary), 6px 6px 0 var(--color-tertiary);
	}
	 90% {
		 text-shadow: 3px 3px 0 var(--color-secondary);
	}
	 100% {
		 text-shadow: none;
	}
}
 @keyframes move {
	 0% {
		 transform: translate(0px, 0px);
	}
	 40% {
		 transform: translate(-12px, -12px);
	}
	 50% {
		 transform: translate(-12px, -12px);
	}
	 60% {
		 transform: translate(-12px, -12px);
	}
	 100% {
		 transform: translate(0px, 0px);
	}
}
/* --------------------------------------------------loading animation --------------------------------------------------*/

.waviy {
  position: relative;
  -webkit-box-reflect: below  linear-gradient(transparent, rgba(0,0,0,.2));
  font-size: calc(1.5rem + 3vw);
}
.waviy span {
  position: relative;
  display: inline-block;
  color: rgb(131, 196, 250);
  text-transform: uppercase;
  animation: waviy 1s infinite;
  animation-delay: calc(.1s * var(--i));
  
}
@keyframes waviy {
  0%,40%,100% {
    transform: translateY(0)
  }
  20% {
    transform: translateY(-20px)
  }
}
/**============================title css ============================================*/

.title {
	 color: rgb(89, 147, 201);
	 text-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 42px #5271ff, 0 0 82px #5271ff, 0 0 92px #5271ff, 0 0 102px #5271ff, 0 0 151px #5271ff;
   font-size: 12px;
	 font-family: "Yellowtail", sans-serif;
   font-size: calc(3.5rem + 3vw);
}
 
 h1, h2 {
	 text-align: center;
	 font-weight: 400;
}
 h1 {
	 font-size: 5.2rem;
	 animation: pulsate 0.11s ease-in-out infinite alternate;
}
 h2 {
	 font-size: 1.8rem;
}
 

/**============================dice css ============================================*/


:root {
  --dark-300: #555;
  --dark-200: #333;
  --dark-100: #111;
  --cube-red: #0046c8;
  --cube-red-2: #0046c8;
  --cube-red-3: #0046c8;
  --cube-red-4: #0046c8;
  --cube-red-5: #0046c8;
  --cube-red-6: #0046c8;
  --dot-color: #fffdfd;
  --darken: rgba(0, 0, 0, 0.4);
}
body {
  background: var(--dark-200);
  background-image: radial-gradient(var(--dark-300), var(--dark-100));
  position: relative;
  min-height: 100vh;
}
.cube-wrap {
  perspective: 1000;
  position: absolute;
  left: 50%;
  top: 80%;
  transform: translate(-50%, -50%);
  perspective: 1000px;
}
.cube {
  position: relative;
  width: 200px;
  height: 200px;
  transform-style: preserve-3d;
  -webkit-animation: spin 7s linear infinite;
          animation: spin 7s linear infinite;
}
.face {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: var(--cube-red);
  background-image: radial-gradient(transparent, var(--darken));
  border: 1px solid var(--cube-red-4);
  -webkit-backface-visibility: visible;
          backface-visibility: visible;
}
.dots {
  display: inline-block;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 0;
  background-color: var(--dot-color);
  position: absolute;
  left: 20px;
  bottom: 20px;
}
.face {
  background-color: #0046c8;
  opacity: 1;
}
.face:nth-child(1) {
  transform: rotateZ(0deg) rotateY(0deg) translateZ(100px);
}
.face:nth-child(1) .dots {
  box-shadow: 120px 0 0 0 var(--dot-color), 0 -120px 0 0 var(--dot-color), 120px -120px 0 0 var(--dot-color), 1px 1px 3px 1px var(--darken), 121px 1px 3px 1px var(--darken), 1px -121px 3px 1px var(--darken), 121px -121px 3px 1px var(--darken);
}
.face:nth-child(2) {
  background-color: var(--cube-red-2);
  transform: rotateZ(0deg) rotateY(0deg) translateZ(-100px);
}
.face:nth-child(2) .dots {
  box-shadow: 120px -120px 0 0 var(--dot-color), 60px -60px 0 0 var(--dot-color), 1px 1px 3px 1px var(--darken), 121px -121px 3px 1px var(--darken), 61px -61px 3px 1px var(--darken);
}
.face:nth-child(3) {
  background-color: var(--cube-red-3);
  transform: rotateZ(0deg) rotateY(90deg) translateZ(-100px);
}
.face:nth-child(3) .dots {
  box-shadow: 120px -120px 0 0 var(--dot-color), 1px 1px 3px 1px var(--darken), 121px -121px 3px 1px var(--darken);
}
.face:nth-child(4) {
  background-color: var(--cube-red-4);
  transform: rotateZ(90deg) rotateY(90deg) translateZ(-100px);
}
.face:nth-child(4) .dots {
  left: 80px;
  bottom: 80px;
  box-shadow: 1px 1px 3px 1px var(--darken);
}
.face:nth-child(5) {
  background-color: var(--cube-red-5);
  transform: rotateZ(0deg) rotateY(-90deg) translateZ(-100px);
}
.face:nth-child(5) .dots {
  box-shadow: 120px 0 0 0 var(--dot-color), 0 -120px 0 0 var(--dot-color), 120px -120px 0 0 var(--dot-color), 60px -60px 0 0 var(--dot-color), 121px 1px 3px 1px var(--darken), 1px -121px 3px 1px var(--darken), 121px -121px 3px 1px var(--darken), 61px -61px 3px 1px var(--darken), 1px 1px 3px 1px var(--darken);
}
.face:nth-child(6) {
  background-color: var(--cube-red-6);
  transform: rotateZ(90deg) rotateY(90deg) translateZ(100px);
}
.face:nth-child(6) .dots {
  box-shadow: 60px 0 0 0 var(--dot-color), 120px 0 0 0 var(--dot-color), 0 -120px 0 0 var(--dot-color), 60px -120px 0 0 var(--dot-color), 120px -120px 0 0 var(--dot-color), 61px 1px 3px 1px var(--darken), 121px 1px 3px 1px var(--darken), 1px -121px 3px 1px var(--darken), 61px -121px 3px 1px var(--darken), 121px -121px 3px 1px var(--darken);
}
@-webkit-keyframes spin {
  0% {
    transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg);
  }
  100% {
    transform: rotateY(1800deg) rotateX(720deg) rotateZ(0deg);
  }
}
@keyframes spin {
  0% {
    transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg);
  }
  100% {
    transform: rotateY(1800deg) rotateX(720deg) rotateZ(0deg);
  }
}


  </style>
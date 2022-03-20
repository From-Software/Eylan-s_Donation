<script>
	import Greeter from './artifacts/contracts/Greeter.sol/Greeter.json';
	import { ethers } from 'ethers';
  import { fade } from 'svelte/transition';
	import { fly } from 'svelte/transition';

  // Scroll animation variables //
	let scroll;

	// Languange button //
	let lang = { spanish: false };
	function toggle() {
		lang.spanish = !lang.spanish;
	}
	// First app variables //

	let firstWord = '';
</script>

<svelte:window bind:scrollY={scroll} />
<main>
  <section class="intro">
		<header>
			<nav>
				<ul>
					<li>
						Itahand Naizir
					</li>
					<li>
						Info
					</li>
					{#if !lang.spanish}
					<li>
						Work
					</li>
					<li>
						Contact
					</li>
					<li on:click={toggle}>
						Español
					</li>
					{:else}
					<li>
						Portafolio
					</li>
					<li>
						Contacto
					</li>
					<li on:click={toggle}>
						English
					</li>
					{/if}
				</ul>
			</nav>
		</header>

		<div class="introduction">
			<h1>
				<p>
					{#if !lang.spanish}
					<span class="highlight-yellow">Itahand Naizir is</span> a software engineer who specializes <span class="highlight-blue">on blockchain development</span>, <span class="highlight-red">decentrilized and autonomous organizations</span> and decentrilized finance.
					{:else}
					<span class="highlight-yellow">Itahand Naizir es</span> un ingeniero en sistema especializado <span class="highlight-blue">en tecnología blockchain</span>, <span class="highlight-red">organizaciones autónomas decentralizadas</span> y finanzas deceentralizadas.
					{/if}

				</p>
			</h1>
		</div>
	</section>

  <section class="info">

		<div class="animated-text">
			<svg viewBox="0 0 600 300">
				<!-- Symbol-->
				<symbol id="s-text">
					<text text-anchor="middle" x="50%" y="35%" dy=".1px">First</text>
					<text text-anchor="middle" x="50%" y="55%" dy=".1px">Second</text>
					<text text-anchor="middle" x="50%" y="75%" dy=".1px">Third</text>
				</symbol>
				<!-- Duplicate symbols-->
				<use class="text" xlink:href="#s-text"></use>
				<use class="text" xlink:href="#s-text"></use>
				<use class="text" xlink:href="#s-text"></use>
				<use class="text" xlink:href="#s-text"></use>
				<use class="text" xlink:href="#s-text"></use>
			</svg>
		</div>
		{#if scroll >700}

		<div class="card" transition:fly="{{ y: 200, duration: 2000 }}">
			<span style="--i:0;"></span>
			<span style="--i:1;"></span>
			<span style="--i:2;"></span>
			<span style="--i:3;"></span>
		  <div class="glass">
			  <div class="input-container">
					<div class="form">
						<input type="text" id="email" class="form__input" autocomplete="off" placeholder=" ">
						<label for="email" class="form__label">First Word</label>
					</div>
					<div class="form">
						<input type="text" id="email" class="form__input" autocomplete="off" placeholder=" ">
						<label for="email" class="form__label">Second Word</label>
					</div>
					<div class="form">
						<input type="text" id="email" class="form__input" autocomplete="off" placeholder=" ">
						<label for="email" class="form__label">Third Word</label>
					</div>
			 </div>
			<h2>Set your phrase<br><i>Deploy to smart contract</i></h2>
		  </div>
		</div>

		{/if}


	</section>

  <section class="card-section">

		<h1>Section 3</h1>

		<div class="form">
			<input type="text" id="email" class="form__input" autocomplete="off" placeholder=" ">
			<label for="email" class="form__label">First Word</label>
		</div>

	</section>

	<section>
		Section 4
	</section>
</main>



<style>

/* Main styles */
@import url(https://fonts.googleapis.com/css?family=Open+Sans:800);
.text {
  fill: none;
  stroke-width: 3;
  stroke-linejoin: round;
  stroke-dasharray: 70 330;
  stroke-dashoffset: 0;
  -webkit-animation: stroke 6s infinite linear;
  animation: stroke 6s infinite linear;
}
.text:nth-child(5n+1) {
  stroke: #F2385A;
  -webkit-animation-delay: -1.2s;
  animation-delay: -1.2s;
}
.text:nth-child(5n+2) {
  stroke: #F5A503;
  -webkit-animation-delay: -2.4s;
  animation-delay: -2.4s;
}
.text:nth-child(5n+3) {
  stroke: #E9F1DF;
  -webkit-animation-delay: -3.6s;
  animation-delay: -3.6s;
}
.text:nth-child(5n+4) {
  stroke: #56D9CD;
  -webkit-animation-delay: -4.8s;
  animation-delay: -4.8s;
}
.text:nth-child(5n+5) {
  stroke: #3AA1BF;
  -webkit-animation-delay: -6s;
  animation-delay: -6s;
}

@-webkit-keyframes stroke {
  100% {
    stroke-dashoffset: -400;
  }
}
@keyframes stroke {
  100% {
    stroke-dashoffset: -400;
  }
}

svg {
  position: relative;
  width: 100%;
  height: 100%;
}
.animated-text {
	height: 50%;
	width: 50%;
  font: 4em/1 Open Sans, Impact;
  text-transform: uppercase;
  margin: 0;
	border-radius: 5%;
}
	main {
		height: 100vh;
		width: 100vw;
		margin: 0;
	}
	section {
		height: 100%;
		width: 100%;
		display: flex;
		justify-content: center;
	}
@media (max-width: 600px) {
	section {
		flex-direction: column;
	}
	.animated-text {
		width: 100%;
		height: 25%;
		font: 5em/1 Open Sans, Impact;
	}
}
	nav {
		position: fixed;
    display: flex;
    width: 100%;
		top: 0;
	}
	nav > ul {
		list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: end;
    width: 100%;
	}
	nav > ul > li {
		color: black;
    margin: 0 0.75rem;
    padding: 0 0.75rem;
    font-size: clamp(0.5rem, 3vw + 1rem, 2rem);
    text-decoration: none;
		cursor: pointer;
	}
	nav > ul > li:nth-child(1) {
		margin-right: auto;
	}
	@media (max-width: 600px) {
		nav > ul {
			justify-content: center;
		}
		nav > ul > li {
			font-size: clamp(1rem, 4vw, 3rem);
		}
		nav > ul > li:nth-child(1) {
			display: none;
		}
	}
	.intro {
		display: flex;
		flex-direction: column;
		justify-content: center;
	}
	.introduction {
		margin: 1rem 20vw;
		transition: 0.5s;
		text-align: center;
	}
	.highlight-red {
  border-radius: 1em 0 1em 0;
  background-image: linear-gradient(
    -100deg,
    rgba(255, 20, 0, 0.2),
    rgba(255, 20, 0, 0.7) 95%,
		rgba(255, 20, 0, 0.1)
  );
}
.highlight-yellow {
  border-radius: 1em 0 1em 0;
  background-image: linear-gradient(
    -100deg,
    rgba(255, 224, 0, 0.2),
    rgba(255, 224, 0, 0.7) 95%,
    rgba(255, 224, 0, 0.1)
  );
}
.highlight-blue {
  border-radius: 1em 0 1em 0;
  background-image: linear-gradient(
    -100deg,
    rgba(0, 20, 255, 0.2),
    rgba(0, 20, 255, 0.7) 95%,
    rgba(0, 20, 255, 0.1)
  );
}

p {
  font-size: 30px;
}
.info {
	display: flex;
	justify-content: flex-start;
	align-items: center;
}
.card-section {
	align-items: center;
}
.card {
	display: flex;
	justify-content: center;
	align-items: center;
	position: relative;
	left: 25%;
}
.card span {
	position: absolute;
	top: 0;
	width: 250px;
	height: 250px;
	display: block;
	background: black;
	border-radius: 50%;
	transform-origin: 125px 0;
	transform: rotate(calc(90deg* var(--i)));
	filter: blur(85px);
	opacity: 0.75;
}
.card span:nth-child(1) {
	background: #01b2fe;
}
.card span:nth-child(2) {
	background: #ff008c;
}
.card span:nth-child(3) {
	background: #ffcd00;
}
.card span:nth-child(4) {
	background: #00c456;
}
.card .glass {
	position: absolute;
	height: 300px;
	width: 450px;
	background: rgba(255,255,255,0.5);
	border-radius: 20px;
	border: 1px solid wheat;
	overflow: hidden;
	display: flex;
	justify-content: flex-start;
	align-items: flex-end;
}
.card .glass::before {
	content: "";
	position: absolute;
	top: 0;
	left: -50%;
	width: 100%;
	height: 100%;
	background: rgba(255,255,255,0.2);
	pointer-events: none;
	transform: skewX(345deg);
}
.card .glass h2{
	padding: 20px;
	font-weight: 400;
	width: 100%;
	background: rgba(255,255,255,0.2);
	color: #333;
	text-align: end;
}
.card .glass h2 i {
	font-weight: 300;
	font-size: 0.75em;
	font-style: normal;
}
.input-container {
	display: flex;
	flex-direction: column;
	align-self: baseline;
	position: absolute;
	margin: 1rem;
}
/* Input Styling */
.form {
  position: relative;
  width: 20rem;
  height: 3rem;
}
.form__input {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 2px solid #e1e5ee;
  border-radius: 0.5rem;
  font-family: inherit;
  font-size: inherit;
  color: black;
  outline: none;
  padding: 1.25rem;
  background: none;
  /* Change border when input focus*/
}
.form__input:hover {
  border-color: #adffff;
}
.form__input:focus {
  border-color: #18ffff;
}
.form__label {
  position: absolute;
  left: 1rem;
  top: 0.8rem;
  padding: 0 0.5rem;
  color: black;
  cursor: text;
	text-align: center;
  transition: top 300ms ease-in-out, left 300ms ease-in-out, font-size 300ms ease-in-out;
	background: none;
}

/*
1. When the input is in the focus state
reduce the size of the label and move upwards

2. Keep label state when content is in input field
*/
.form__input:focus ~ .form__label,
.form__input:not(:placeholder-shown).form__input:not(:focus) ~ .form__label {
  font-size: 0.8rem;
  left: 100%;
	overflow: visible;
}
</style>
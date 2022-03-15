<script>
	import Greeter from './artifacts/contracts/Greeter.sol/Greeter.json';
	import { ethers } from 'ethers';

  let lang = { spanish: false };

	function toggle() {
		lang.spanish = !lang.spanish;
	}

  const address = "0x5FbDB2315678afecb367f032d93F642f64180aa3";
  let greeter = '';
	let actual;
	async function requestAccount() {
    await window.ethereum.request({ method: 'eth_requestAccounts' });
  }
  async function fetchGreeting() {
    if (typeof window.ethereum !== 'undefined') {
      const provider = new ethers.providers.Web3Provider(window.ethereum)
      console.log({ provider })
      const contract = new ethers.Contract(address, Greeter.abi, provider)
      try {
        const data = await contract.greet()
        console.log('data: ', data)
				actual = data;
      } catch (err) {
        console.log("Error: ", err)
      }
    }
  }
	async function setGreeting() {
    if (!greeting) return
    if (typeof window.ethereum !== 'undefined') {
      await requestAccount()
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      console.log({ provider })
      const signer = provider.getSigner()
      const contract = new ethers.Contract(address, Greeter.abi, signer)
      const transaction = await contract.setGreeting(greeting)
      await transaction.wait()
      fetchGreeting()
    }
  }
</script>

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
					<span class="highlight-yellow">Itahand Naizir is</span> a software engineer who specializes <span class="highlight-blue">on blockchain development</span>, dec<span class="highlight-red">entrilized and autonomous organizations</span> and decentrilized finance.
					{:else}
					<span class="highlight-yellow">Itahand Naizir es</span> un ingeniero en sistema especializado <span class="highlight-blue">en tecnología blockchain</span>, org<span class="highlight-red">anizaciones autónomas decentralizadas</span> y finanzas deceentralizadas.
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

		<div class="words-input">
			<h1>Put first word here</h1>
			<h1>Put second word here</h1>
			<h1>Put thirds word here</h1>
			<button on:click={fetchGreeting}>Fetch Greeting</button>
			<button on:click={setGreeting}>Set Greeting</button>
			<input bind:value={firstWord} placeholder="First Word Here">
			<input bind:value={secondWord} placeholder="Second Word Here">
			<input bind:value={thirdWord} placeholder="Third Word Here">
			<h1>{firstWord}{secondWord}{thirdWord}</h1>
			<h1>The current phrase on the Blockchain is: "{actual}"</h1>
		</div>

	</section>

  <section>
		Section 3
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
}
.words-input {
	height: 50%;
	display: flex;
	flex-direction: column;
	justify-content: space-around;
}
	main {
		text-align: center;
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
	}
	.highlight-red {
  border-radius: 1em 0 1em 0;
  background-image: linear-gradient(
    -100deg,
    rgba(255, 20, 0, 0.2),
    rgba(255, 20, 0, 0.7) 95%,gba(255, 20, 0, 0.1)
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
</style>
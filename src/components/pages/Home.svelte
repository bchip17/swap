<script>
	import Volume from '../Volume.svelte'

	import { EXTERNAL_ICON, DISCORD_ICON, TWITTER_ICON, TELEGRAM_ICON, GITHUB_ICON, ARBITRUM_ICON, CHECKMARK_ICON, MEDIUM_ICON } from '../../lib/icons'

	import { CURRENCY_LOGOS } from '../../lib/constants'
	import { PRODUCTS } from '../../lib/products'
	import { getChainData, formatCurrency } from '../../lib/utils'

	let currencies = getChainData('currencies');

	amplitude.getInstance().logEvent('Home');

</script>
<style>

	.home-wrap {
		background-color: var(--eerie-black);
		background: url("bg.jpg") no-repeat fixed center;
		background-size: cover;
		min-height: 100vh;
	}

	.home {
		margin: 0 auto;
		max-width: 1200px;
		padding: var(--base-padding);
		padding-bottom: 36px;
	}

	.hero {
		display: flex;
		padding: 30px 0;
	}

	@media (max-width: 800px) {
		.hero {
			flex-direction: column;
		}
	}

		.hero-inner {		
			display: grid;
			grid-auto-flow: row;
			grid-gap: 36px;
		}

		.main-title {
		}

		.main-title img {
			height: 60px;
		}

		.tagline {
			line-height: 1.348;
			font-size: 260%;
			font-weight: 700;
			max-width: 500px;
		}
		.tagline1 {
		    line-height: 1.3;
    		font-size: 146%;
    		max-width: 500px;
			margin: 20px 0;
		}

		.subhead {
			line-height: 1.518;
			font-size: 120%;
			font-weight: 400;
			max-width: 330px;
			margin: 0 auto;
			margin-top: 12px;
		}

		.pill {
			font-size: 110%;
			padding: 8px 14px;
			border-radius: 6px;
			font-weight: 600;
			display: inline-block;
			margin-top: 20px;
			margin-right: 12px;
			background-color: var(--jet);
			color: #fff;
		}

		.chains {
			display: flex;
			align-items: center;
			justify-content: center;
			font-size: 90%;
			font-weight: 500;
		}
		.chains :global(svg) {
			height: 22px;
			margin-right: 4px;
			margin-left: 8px;
		}

		.button-wrap {
		}

		.button {
			padding: 16px 26px;
			border-radius: var(--base-radius);
			font-weight: 650;
			font-size: 120%;
			color: var(--green-dark);
			background-color: var(--green);
			display: inline-block;
		}
		.button:hover {
			background-color: var(--green-dim);
		}

		.volume .label {
			color: var(--sonic-silver);
			margin-top: 10px;
		}

		.volume .value {
			font-weight: 700;
			font-size: 110%;
		}

	.supported {
		padding: 12px 36px;
		padding-right: 0;
		text-align: right;
		flex: 1;
	}

	@media (max-width: 800px) {
		.supported {
			text-align: left;
			padding: 36px 0 0;
		}
	}

		.title {
			margin-top: 10px;
			color: var(--sonic-silver);
			margin-bottom: 36px;
		}

		.title:last-child {
			margin-bottom: 0;
		}

		.content img, .content :global(svg) {
			width: 42px;
			margin-left: 16px;
		}

		@media (max-width: 800px) {
			.content img, .content :global(svg) {
				margin-left: 0;
				margin-right: 16px;
			}
		}


	.links {
		padding-top: 18px;
		line-height: 2;
		text-align: center;
	}
	.links a {
		margin-right: 16px;
		color: var(--sonic-silver);
		font-size: 90%;
		white-space: nowrap;
	}
	.links a:hover {
		color: var(--green);
	}
	.community {
		padding-top: 5px;
		text-align: center;
		align-items: center;
	}

	.community a {
		margin-right: 24px;
	}

	.community :global(svg) {
		height: 24px;
		fill: currentColor;
	}

	.sep {
		width: 40px;
		height: 2px;
		background-color: var(--onyx);
	}

	.mountains {
		opacity: 0.75;
		width: 100%;
	}

	.mountains img {
		max-width: 100%;
	}
	.trade-mark {
		color: var(--blue-chip-color);
		font-weight:bold;
	}

</style>

<div class='home-wrap'>

	<div class='home'>

		<div class='hero'>

			<div class='hero-inner'>
				
				<div>
					<div class='tagline'>Decentralized Perpetual Exchange</div>
					<div class="tagline1"><span class="trade-mark">BlueChip</span> is the first fully-permissionless DEX for trading perpetual contracts, powered by <span class="trade-mark">BlueChip</span>'s revolutionary AMM technology.</div>
					<div class="pill">0% Fees</div>
					<div class="pill">50× Leverage</div>
					
				</div>

				<div class='button-wrap'>
					<a class='button' href='#/trade'>Trade</a>
				</div>

				<div class='volume'>
					<div class='value'><Volume/></div>
					<div class='label'>Protocol Volume</div>
				</div>

			</div>

			<div class='supported'>

				<div class='content'>
					{#each Object.entries(PRODUCTS) as [_productId, info]}
						<img src={info.logo} title={`${_productId}`}>
					{/each}
				</div>
				<div class='title'>Supported Products</div>

				<div class='content'>
					{#each Object.entries(currencies) as [_currencyLabel, info]}
						<img src={CURRENCY_LOGOS[_currencyLabel]} title={`${formatCurrency(_currencyLabel)}`}>
					{/each}
				</div>
				<div class='title'>Supported Collateral</div>

				<div class='content'>
					<span title='Arbitrum'>{@html ARBITRUM_ICON}</span>
				</div>
				<div class='title'>Supported Networks</div>

			</div>

		</div>

		<div class='sep'>&nbsp;</div>
		
		<div class='community'>
			<a href='https://medium.com/@bcpdarkofficial' target='_blank' title='Medium'>{@html MEDIUM_ICON}</a>
			<a href='https://discord.gg/tJB69HJ7' target='_blank' title='Discord'>{@html DISCORD_ICON}</a>
			<a href='https://t.me/bcpdarkofficial' target='_blank' title='Telegram'>{@html TELEGRAM_ICON}</a>
			<a href='https://twitter.com/BlueChi47537205' target='_blank' title='Twitter'>{@html TWITTER_ICON}</a>
			<a href='https://github.com/bluechip17' target='_blank' title='Github'>{@html GITHUB_ICON}</a>
		</div>

		<div class='links'>
			<a href='#/buy'>Buy BCP</a>
			<a href='https://blueswap.net/whitepaper.pdf' target='_blank'>Whitepapers</a>
			<a href='https://docs.blueswap.net/' target='_blank'>Docs</a>
			<a href='https://www.tokenterminal.com/terminal/projects/bcp' target='_blank'>Token Terminal</a>
			<a href='https://defillama.com/protocol/bcp' target='_blank'>Defi Llama</a>
			<a href='https://www.immunefi.com/bounty/bcp' target='_blank'>Immunefi</a>
		</div>

	</div>


</div>
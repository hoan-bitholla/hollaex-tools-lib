
<!-- PROJECT LOGO -->
<br />
<p align="center">

  <h3 align="center">HollaEx Tools Library</h3>

  <p align="center">
    Tools Library for developing HollaEx Kit enabled Exchanges
    <br />
    <a href="https://github.com/github_username/repo_name"><strong>Explore the docs »</strong></a>
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

Here's a blank template to get started:
**To avoid retyping too much info. Do a search and replace with your text editor for the following:**
`github_username`, `repo_name`, `twitter_handle`, `email`, `project_title`, `project_description`

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

This Tools Library will only work with the [HollaEx Kit]().

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/bitholla/hollaex-tools-lib.git
   ```
2. Install NPM packages
   ```sh
   npm install hollaex-tools-lib
   ```



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

### Importing Library

```javascript
const tools = require('hollaex-tools-lib');
```

### Common Functions

- getUserByEmail(email, [rawData = true], [networkData = false])
- getUserByKitId(kit_id, [rawData = true], [networkData = false])
- getUserByNetworkId(network_id, [rawData = true], [networkData = false])
- getUserTier(user_id);
- createUser(email, password, [opts = { role: 'user', id: null }])
- getKitConfig()
- getKitSecrets()
- getKitCoins()
- getKitCoinsConfig()
- getKitPairs()
- getKitPairsConfig()
- createUserOrderByKitId()


### Full list of functions

#### Common functions

- `subscribedToCoin(coin)`
  - Checks to see if the exchange is subscribed to a specific coin
  - Returns boolean value
	```javascript
	tools.subscribedToCoin('xht');
	```
- `subscribedToPair(pair)`
  - Checks to see if the exchange is subscribed to a specific pair
  - Returns boolean value
	```javascript
	tools.subscribedToPair('xht-usdt');
	```
- `getKitCoin(coin)`
  - Gets data for a specific coin
  - Returns coin object
	```javascript
	tools.getKitCoin('xht');

	/*
		{
			id: 1,
			fullname: "HollaEx",
			symbol: "xht",
			active: true,
			verified: true,
			allow_deposit: true,
			allow_withdrawal: true,
			withdrawal_fee: 0,
			min: 0.0001,
			max: 100000,
			increment_unit: 0.0001,
			created_at: "2020-02-03T10:19:10.857Z",
			updated_at: "2020-02-03T10:19:10.857Z",
			logo: null,
			code: "xht",
			is_public: true,
			meta: { },
			estimated_price: null,
			description: null,
			type: "blockchain",
			network: null,
			standard: null
		}
	*/
	```
- `getKitCoins()`
  - Gets all coins for the exchange
  - Returns array with all coins
	```javascript
	tools.getKitCoins();

	/*
		[
			'xht',
			'btc',
			'eth',
			...
		]
	*/
	```
- `getKitCoinsConfig(coin)`
  - Gets all coins and their configurations
  - Returns object with coins as keys
	```javascript
	tools.getKitCoinsConfig('xht');

	/*
		{
			usdt: {...},
			xht: {...},
			...
		}
	*/
	```
- `getKitPair(pair)`
  - Gets data for a specific pair
  - Returns pair object
	```javascript
	tools.getKitPair('xht-usdt');

	/*
		{
			id: 1,
			name: "xht-usdt",
			pair_base: "xht",
			pair_2: "usdt",
			min_size: 0.1,
			max_size: 100000,
			min_price: 0.001,
			max_price: 1000000,
			increment_size: 0.001,
			increment_price: 0.01,
			active: true,
			verified: true,
			code: "xht-usdt",
			is_public: true,
			estimated_price: null,
			created_at: "2020-02-03T10:19:10.846Z",
			updated_at: "2020-02-03T10:19:10.846Z"
		}
	*/
	```
- `getKitPairs()`
  - Gets all pairs for the exchange
  - Returns array with all pairs
	```javascript
	tools.getKitPairs();

	/*
		[
			'xht-usdt',
			'btc-usdt',
			'eth-usdt',
			...
		]
	*/
	```
- `getKitPairsConfig(pair)`
  - Gets all pairs and their configurations
  - Returns object with pairs as keys
	```javascript
	tools.getKitPairsConfig('xht-usdt');

	/*
		{
			'xht-usdt': {...},
			'btc-usdt': {...},
			...
		}
	*/
	```
- `isValidTierLevel(level)`
  - Checks to see if the exchange includes a specific tier level
  - Returns boolean value
	```javascript
	tools.isValidTierLevel(1);
	```
- `getKitTier(tier)`
  - Gets tier configurations
  - Returns object tier configurations
	```javascript
	tools.getKitTier(1);

	/*
		{
			id: 1,
			name: "basic",
			icon: "",
			description: "basic tier",
			deposit_limit: 0.1,
			withdrawal_limit: 0.1,
			fees: {
				maker: {
					xht-usdt: 1.4,
					xmr-usdt: 0.2,
					eth-usdt: 0.2,
					btc-usdt: 0.2
				},
				taker: {
					xht-usdt: 2.7,
					xmr-usdt: 0.2,
					eth-usdt: 0.2,
					btc-usdt: 0.2
				}
			},
			note: "<ul> <li>email verification</li> </ul> ",
			created_at: "2020-10-28T02:00:57.128Z",
			updated_at: "2020-11-28T05:31:30.599Z"
		}
	*/
	```
- `getKitTiers()`
  - Gets all tiers and their configurations
  - Returns object with tiers as keys
	```javascript
	tools.getKitTiers();

	/*
		{
			1: {...},
			2: {...},
			...
		}
	*/
	```
- `getKitConfig()`
  - Gets exchange configurations
  - Returns object
	```javascript
	tools.getKitConfig();

	/*
		{
		"meta": {...},
		"color": {...},
		"icons": {...},
		"links": {...},
		"title": "string",
		"captcha": {
			"site_key": ""
		},
		"strings": {...},
		"api_name": "string",
		"defaults": {
			"theme": "string",
			"language": "string"
		},
		"interface": {
			"type": "string"
		},
		"logo_image": "string",
		"description": "string",
		"native_currency": "string",
		"setup_completed": boolean,
		"valid_languages": "string",
		"new_user_is_activated": boolean,
		"info": {
			"name": "string",
			"active": boolean,
			"url": "string",
			"is_trial": boolean,
			"created_at": "string",
			"expiry": "string",
			"status": boolean,
			"initialized": boolean
		}
	}
	*/
	```
- `getKitSecrets()`
  - Gets exchange configuration secrets
  - Returns object
	```javascript
	tools.getKitSecrets();

	/*
		{
			"smtp": {...},
			"emails": {...},
			"captcha": {...},
			"security": {...},
			"admin_whitelist": [],
			"allowed_domains": []
		}
	*/
	```
- `getFrozenUsers()`
  - Gets exchange's frozen users
  - Returns object with user IDs as keys
	```javascript
	tools.getFrozenUsers();

	/*
		{
			'4': true,
			'7': true,
			...
		}
	*/
	```
- `updateKitConfigSecrets(data = {}, scopes = [])`
  - Updates exchange configurations and secrets
  - Scopes is the scope of the user making this action in an array
  - Returns promise with newly update kit and secrets
	```javascript
	tools.updateKitConfigSecrets(
		{
			kit: {
				defaults: {
					theme: 'dark',
					language: 'en'
				}
			},
			secrets: {
				allowed_domains: [
					'https://google.com'
				]
			}
		},
		['admin']
	)
		.then((data) => {
			/*
				{
					"kit": {
						"meta": {...},
						"color": {...},
						"icons": {...},
						"links": {...},
						"title": "",
						"captcha": {...},
						"strings": {...},
						"api_name": "hollaex-kit",
						"defaults": {
							"theme": "dark",
							"language": "en"
						},
						"interface": {...},
						"description": "",
						"valid_languages": "",
						"new_user_is_activated": true
					},
					"secrets": {
						"smtp": {...},
						"broker": {...},
						"emails": {...},
						"captcha": {...},
						"security": {...},
						"admin_whitelist": [],
						"allowed_domains": ['https://google.com'],
						"setup_completed": false,
						"exchange_credentials_set": true
					}
				}
			*/
		});
	```
- `sendEmailToSupport(email, category, subject, description)`
  - Send an email to support account of exchange
  - Returns promise
	```javascript
	tools.sendEmailToSupport(
		'person@bitholla.com',
		'support',
		'Support Requested',
		'Need support'
	)
		.then((data) => {
			///continue
		});
	```
- `getNetworkKeySecret()`
  - Get network key and secret for exchange
  - Returns promise with apiKey and apiSecret
	```javascript
	tools.getNetworkKeySecret()
		.then((data) => {
			/*
				{
					apiKey: "",
					apiSecret: ""
				}
			*/
		});
	```
- `getAssetsPrices(assets = [] [,quote, amount])`
  - Get converted asset prices
  - Returns promise with converted asset prices
	```javascript
	tools.getAssetsPrices(['xht', 'btc'], 'usdt', 1)
		.then((data) => {
			/*
				{
					btc: 20000,
					xht: 0.10
				}
			*/
		});
	```
- `sendEmail(type, receiver, data, userSettings = {}, domain)`
  - Sends an email
  - Returns resolved promise after sending the email
	```javascript
	tools.sendEmail(
		'login',
		'person@bitholla.com',
		{
			date: '',
			time: '',
			device: ''
		}
		{ language: 'en' },
		'https://bitholla.com'
	)
		.then((data) => {
			//continue
		});
	```
- `getTicker(symbol)`
  - Get ticker data for a symbol
  - Returns promise with ticker info
	```javascript
	tools.getTicker('xht-usdt')
		.then((data) => {
			/*
				{
					"open": 0,
					"close": 0,
					"high": 0,
					"low": 0,
					"last": 0,
					"volume": 0
				}
			*/
		});
	```
- `getTickers()`
  - Get ticker data for all symbols
  - Returns promise with tickers info
	```javascript
	tools.getTicker('xht-usdt')
		.then((data) => {
			/*
				{
					"xht-usdt": {...},
					"btc-usdt": {...},
					...
				}
			*/
		});
	```
- `getOrderbook(symbol)`
  - Get top orderbook data for a symbol
  - Returns promise with orderbook info
	```javascript
	tools.getOrderbook('xht-usdt')
		.then((data) => {
			/*
				{
					"xht-usdt": {
						"bids": [...],
						"asks": [...],
						"timestamp": "2020-12-18T01:48:06.559Z"
					}
				}
			*/
		});
	```
- `getOrderbooks()`
  - Get top orderbook data for all symbols
  - Returns promise with orderbook info
	```javascript
	tools.getOrderbook()
		.then((data) => {
			/*
				{
					"xht-usdt": {...},
					"btc-usdt": {...},
					...
				}
			*/
		});
	```
- `getPublicTrades([symbol])`
  - Get public trades data
  - Pass symbol to get all trades data
  - Returns promise with trades info
	```javascript
	tools.getPublicTrades()
		.then((data) => {
			/*
				{
					"xht-usdt": [
						{
							"size": 0.1,
							"price": 20,
							"timestamp": "2020-12-15T06:45:27.450Z",
							"side": "buy"
						},
						...
					],
					"btc-usdt": [
						{
							"size": 0.1,
							"price": 20000,
							"timestamp": "2020-12-15T06:45:27.450Z",
							"side": "buy"
						},
						...
					],
					...
				}
			*/
		});
	```
- `getChart(from, to, symbol, resolution)`
  - Get chart data from network
  - Returns promise with chart data
	```javascript
	tools.getEngineChart(1605668071, 1608260132, 'btc-usdt', 'D')
		.then((data) => {
			/*
				[
					{
						time: "2020-11-19T00:00:00.000Z",
						close: 17811.9,
						high: 18130.15,
						low: 17349.75,
						open: 17776.75,
						symbol: "btc-usdt",
						volume: 116.2818
					},
					...
				]
			*/
		});
	```
- `getCharts(from, to, resolution)`
  - Get chart data from network for all symbols
  - Returns promise with chart data
	```javascript
	tools.getEngineCharts(1605668071, 1608260132, 'D')
		.then((data) => {
			/*
				{
					'xht-usdt': [...],
					'btc-usdt': [...],
					...
				}
			*/
		});
	```
- `getUdfConfig()`
  - Get udf configuration for chart on network
  - Returns promise with config data
	```javascript
	tools.getUdfConfig()
		.then((data) => {
			/*
				{
					"supported_resolutions": [
						"60",
						"1D"
					],
					"supports_group_request": false,
					"supports_marks": false,
					"supports_search": true,
					"supports_timescale_marks": false
				}
			*/
		});
	```
- `getUdfHistory()`
  - Get udf configuration for chart on network
  - Returns promise with data
	```javascript
	tools.getUdfConfig()
		.then((data) => {
			/*
				{
					c: [..],
					h: [...],
					l: [...],
					o: [...],
					t: [...],
					v: [...],
					s: "ok"
				}
			*/
		});
	```
- `getUdfSymbols('xht-usdt')`
  - Get udf symbol chart data
  - Returns promise with data
	```javascript
	tools.getUdfSymbols('xht-usdt')
		.then((data) => {
			/*
				{
					"name": "HollaEx:XHT-USDT",
					"ticker": "xht-usdt",
					"exchange": "HollaEx",
					"has_intraday": true,
					"has_daily": true,
					"has_weekly_and_monthly": true,
					"session": "24x7",
					"regular_session": "24x7",
					"pricescale": 1,
					"volume_precision": 2,
					"has_empty_bars": true
				}
			*/
		});
	```
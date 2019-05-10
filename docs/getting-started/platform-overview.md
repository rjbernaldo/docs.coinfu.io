# Platform overview

> `coinfu.io` is a no code platform to build, backtest, and run automated cryptocurrency based trading strategies.

Let's start with Our platform's two main components: `Bots` & `Strategies`.

## Bots
Think of bots as task runners. They are the entities which run your strategy. They have configurable properties like which market to run on, on what exchange, etc.

Actions dictated by the strategy and taken by the bot are recorded or updated as `positions`. Positions are composed of market orders called `entries`.

Bots can perform different actions depending on how many entries it has in the market. There are three actions available on a position: `enter` (go short or long), `add unit` (pyramid into a position), and `exit` (either via strategy or via stop loss).

Number of entries | Available actions
--- | ---
N = 0 | `enter`
0 < N < max | `add unit` or `exit`
N = max | `exit`

When a bot is running, actions are executed on an interval basis every X minute(s) depending on it's type:

Action type | Default interval
--- | ---
`enter` | Run every 30 minutes
`add unit` | Run every 30 minutes
`exit` | Run every minute

Lastly, a bot has 3 different modes:

Mode | Description
--- | ---
`inactive` | As the name suggests, the bot is not running. It does not perform any actions. This is usually used in developing strategies and on running backtests.
`signals` | The bot is running and actions are performed _but it does not execute orders on the exchange_. This is usually used to provide signals to the trader which he/she can then decide to execute the manually.
`live` | The bot is running, actions are performed, buy and sell orders are executed on the exchange.

## Strategies
Strategies contain the core logic of how you interact with the markets. These are broken down into three segments: `enter strategy`, `exit strategy`, and `money management`.
  - Enter strategies are performed 

Crafting strategies are done using the following components: `events`, `gateways`, and `activity`.


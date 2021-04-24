# Quack Slack Currency

## Vision

Quack is a digital currency built on the Etheruem ERC-20 standard. It will be deployed to an Ethereum testnet and used as a workspace specific currency in slack. This will allow members of the workspace to show appreciation for one another by tipping, use the coins to show support for proposals and hopefully purchased digital artwork created by other members. This will incentivize acts of appreciation, encourage camaraderie and make slack more fun and interactive.

## Scope

### IN

The front end of our application will be comprised of a set of slack interfaces accessed with a simple slash command in the text input. From this menu, holders of the coin will be able to:

-   transfer coins to another member in the workspace
-   mint new coins that will be distributed to all current holders
-   burn coins to show support for a proposal
-   draft a proposal for a vote
-   withdraw coins into a crytocurrency wallet such as meta-mask

### OUT

These features will not be included.

-   our currency will not be deployed to the ethereum mainnet and will not be worth real money
-   users will never have to pay real money
-   our currency won't be mined

### MVP

Our app will provide a way to exchange our proprietary digital currency using slack. All transactions will be recorded on the blockchain via a smart contract deployed to a testnet. This currency will be functional and can inflate. Anything that costs coins will adjust according to inflation.

### STRETCH GOALS

-   integrate with other class slack currency, allow swapping and/or staking
-   make coin ERC-20 compliant so users and hold in wallets
-   integrate with terminal art app so artwork can be purchased, minted into an NFT and given to buyer

## Functional Requirements

1. admins will distribute initial disbursement to users
2. admins shall not access the currency outside of slack functions after initial disbursement
3. users can transfer, receive, burn and mint new currency
4. users can check their own balance, but not the balance of others

## Non-Functional Requirements

### Security

-   only admins will have access to slack and backend endpoints
-   only users slack ids will be stored, no other sensitive information

### Usability

-   the interface will be built into slack and therefor very useable for the daily slack user
-   users wont have to deal with crypto wallets as balances and such are dealt with in slack

## Data Flow

When the users instigates the slash command in slack, their are given a selection of options. Each option will touch a different endpoint in our slack app. The slack endpoint will send a request to our Deno backend which will then, using the Web3 library, will make the appropriate request to the Ethereum blockchain and our smart contract. We will then forward the response from the event emitters in our deployed smart contract to our backend, parse the results and send the appropriate message to the user via the slack app.

# Revolv tokenlists

This is a general purpose tokenlist generation app that Revolv uses to
generate it's
[tokenlist](https://github.com/balancer/tokenlists/blob/main/generated/balancer.tokenlist.json).

## Make changes to the Revolv tokenlist

To make changes to the revolv tokenlist edit the files in
[src/tokenlists/balancer](https://github.com/balancer/tokenlists/tree/main/src/tokenlists/balancer).

1. `metadata.ts` - Edit this to change the highlevel tokenlist metadata.
1. `tokens/<network>.ts` - Edit this to add or remove tokens from the generated tokenlist. E.g Tokens for Arbitrum go in `tokens/arbitrum.ts`, tokens for Ethereum go in `tokens/ethereum.ts`. 
1. `overwrites.ts` - Edit this to overwrite any token data that is incorrect
   when generated automatically.

Once changes are made, the tokenlist can be regenerated by running:

```shell
npm run generate
```

This updates the generated file at `/generated/balancer.tokenlist.json`

**However, you do not need to run this command locally. Simply make changes to
the mentioned files and merge them with the `main` branch. Following this, an
autogenerated PR will be created to update the generated tokenlist files.**

## Create a new tokenlist

Although this repo is primarily for maintaing the balancer.tokenlist.json file,
it can be forked and used to generate any kind of tokenlist. Simply run:

```shell
npm run tokenlist:create my-new-tokenlist
```

This will create a new template tokenlist in `/src/tokenlists` with the
necessary files. Then, just add token addresses to the `tokens.ts` file and run
`npm run generate` to generate your tokenlist json file.

## Development

To run the `generate` command locally or in the Github actions of a fork you
will need to add these ENV variables:

```
INFURA_KEY=xxx
POKT_KEY=xxx
```

You'll need to sign up to each of those services to get keys:

- https://www.infura.io/
- https://www.pokt.network/

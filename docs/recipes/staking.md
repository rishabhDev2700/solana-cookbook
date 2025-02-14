---
title: Staking
head:
  - - meta
    - name: title
      content: Solana Cookbook | Staking
  - - meta
    - name: og:title
      content: Solana Cookbook | Staking
  - - meta
    - name: description
      content: stake SOL and earn rewards for helping secure the network.
  - - meta
    - name: og:description
      content: Stake SOL and earn rewards for helping secure the network. Learn more about Creating Stake Accounts, Delegate Stake, Withdraw Stake and more Recipes for Building on Solana at The Solana cookbook.
  - - meta
    - name: og:image
      content: https://solanacookbook.com/cookbook-sharing-card.png
  - - meta
    - name: og:image:alt
      content: Solana splash card
  - - meta
    - name: twitter:card
      content: summary
  - - meta
    - name: twitter:site
      content: "@solanacookbook"
  - - meta
    - name: twitter:image
      content: "https://solanacookbook.com/cookbook-sharing-card.png"
  - - meta
    - name: robots
      content: index,follow,noodp
  - - meta
    - name: googlebot
      content: index,follow
footer: MIT Licensed
---

# Staking



## Get Current Validators

We can stake SOL and earn rewards for helping secure the network. To stake, we delegate SOL to validators who in turn process transactions.

<CodeGroup>
  <CodeGroupItem title="TS" active>

@[code](@/code/staking/get-current-validators/get-current-validators.en.ts)

  </CodeGroupItem>
  <CodeGroupItem title="CLI">

@[code](@/code/staking/get-current-validators/get-current-validators.en.sh)

  </CodeGroupItem>
</CodeGroup>

## Create Stake Account

All staking instructions are handled by the [Stake Program](https://docs.solana.com/developing/runtime-facilities/programs#stake-program). To begin, we create a [Stake Account](https://docs.solana.com/staking/stake-accounts) which is created and managed differently than a standard [system account](accounts.md#create-a-system-account). In particular, we must set the account's `Stake Authority` and `Withdrawal Authority`.

<SolanaCodeGroup>
  <SolanaCodeGroupItem title="TS" active>

  <template v-slot:default>

@[code](@/code/staking/create-stake-account/create-stake-account.en.ts)

  </template>

  <template v-slot:preview>

@[code](@/code/staking/create-stake-account/create-stake-account.preview.en.ts)

  </template>

  </SolanaCodeGroupItem>
</SolanaCodeGroup>

## Delegate Stake

Once a stake account is funded, the `Stake Authority` can delegate it to a validator. Each stake account can only be delegated to one validator at a time. In addition, all tokens in the account must be either delegated or un-delegated. Once delegated, it takes several epochs for a stake account to become active.

<SolanaCodeGroup>
  <SolanaCodeGroupItem title="TS" active>

  <template v-slot:default>

@[code](@/code/staking/delegate-stake/delegate-stake.en.ts)

  </template>

  <template v-slot:preview>

@[code](@/code/staking/delegate-stake/delegate-stake.preview.en.ts)

  </template>

  </SolanaCodeGroupItem>
</SolanaCodeGroup>

## Deactivate Stake

At anytime after a stake account is delegated, the `Stake Authority` can choose to deactivate the account. Deactivation can take several epochs to complete, and is required before any SOL is withdrawn.

<SolanaCodeGroup>
  <SolanaCodeGroupItem title="TS" active>

  <template v-slot:default>

@[code](@/code/staking/deactivate-stake/deactivate-stake.en.ts)

  </template>

  <template v-slot:preview>

@[code](@/code/staking/deactivate-stake/deactivate-stake.preview.en.ts)

  </template>

  </SolanaCodeGroupItem>
</SolanaCodeGroup>

## Withdraw Stake

Once deactivated, the `Withdrawal Authority` can withdraw SOL back to a system account. Once a stake account is no longer delegated and has a balance of 0 SOL, it is effectively destroyed.

<!-- <CodeGroup>
  <CodeGroupItem title="TS" active> -->
<SolanaCodeGroup>
  <SolanaCodeGroupItem title="TS" active>

  <template v-slot:default>

@[code](@/code/staking/withdraw-stake/withdraw-stake.en.ts)

  </template>

  <template v-slot:preview>

@[code](@/code/staking/withdraw-stake/withdraw-stake.preview.en.ts)

  </template>
  </SolanaCodeGroupItem>
</SolanaCodeGroup>

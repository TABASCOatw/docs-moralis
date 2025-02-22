---
title: "How to get the native balance of an ERC20 token vault"
slug: "../how-to-get-the-native-balance-of-a-smart-contract-vault"
description: "Learn how to get the native balance of a ERC20 token vault using the Moralis Wallet API."
sidebar_label: "Get native balance of ERC20 token vault"
---

## Step 1: Setup Moralis

Read the article [Setting Up Moralis: Getting Started](/web3-data-api/evm/get-your-api-key) and make sure to finish all the steps. Only after that you can go ahead to complete this guide.

## Step 2: Get the native balance of an address

In order to get the native balance of an ERC20 token vault, Moralis provides you the [getNativeBalance](/web3-data-api/evm/reference/get-native-balance) API endpoint.

Here you'll need two parameters: `address` and `chain`.

Once you have obtained both the `address` and `chain`, you can copy the following code:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs groupId="programming-language">
  <TabItem value="javascript" label="index.js (JavaScript)" default>

```javascript index.js
const Moralis = require("moralis").default;
const { EvmChain } = require("@moralisweb3/common-evm-utils");

const runApp = async() => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });

  // address of ERC20 token vault, e.g. WETH token address
  const address = '0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2';

  const chain = EvmChain.ETHEREUM;

  const response = await Moralis.EvmApi.balance.getNativeBalance({
    address,
    chain,
  });

  console.log(response.toJSON());
}

runApp();
```

</TabItem>
<TabItem value="typescript" label="index.ts (TypeScript)">

```typescript index.ts
import Moralis from "moralis";
import { EvmChain } from "@moralisweb3/common-evm-utils";

const runApp = async() => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });

  // address of ERC20 token vault, e.g. WETH token address
  const address = "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2";

  const chain = EvmChain.ETHEREUM;

  const response = await Moralis.EvmApi.balance.getNativeBalance({
    address,
    chain,
  });

  console.log(response.toJSON());
};

runApp();
```

</TabItem>
<TabItem value="python" label="index.py (Python)">

```python index.py
from moralis import evm_api

api_key = "YOUR_API_KEY"

params = {
    # address of ERC20 token vault, e.g. WETH token address
    "address": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2",
    "chain": "eth",
}

result = evm_api.balance.get_native_balance(
    api_key=api_key,
    params=params,
)

print(result)
```

</TabItem>
</Tabs>

## Step 3: Run the script

import RunTheScript from '/docs/partials/\_run-the-script.mdx';

<RunTheScript />

In your terminal, you should see the following JSON response:

```json
[
  {
    "balance": "3989233490541891348056490"
  }
]
```

Congratulations 🥳 You just got the native balance of an ERC20 token vault with just a few lines of code using the Moralis Wallet API!

## Youtube Video

https://www.youtube.com/watch?v=sL5t07JE0aE

## API Reference

If you want to know more details on the endpoint and optional parameters, check out:

- [getNativeBalance](/web3-data-api/evm/reference/get-native-balance)

## Support

If you face any trouble following the tutorial, feel free to reach out to our community engineers in our [Discord](https://moralis.io/discord) or [Forum](https://forum.moralis.io) to get 24/7 developer support.

---
description: Tutorial on how to use next price orders on Kwenta
---

# How to use Next Price

Traders on Kwenta will see a new addition to order types available on Kwenta. Traders can take advantage of **Next Price Orders** and their matching lower bps fees by heading to Kwenta, navigating to the Futures tab, and connecting their wallet.​

![](<../../../.gitbook/assets/HLPpQms3RhEKT7e1YuxCp (1).png>)

Once connected traders can select the asset they wish to trade from the Asset Selection Dropdown to be taken to the perspective markets dashboard and begin trading. Once traders deposit sUSD into the market.

In the Order Entry panel, you’ll see two types of orders: Market and Next Price. The existing Market Order will execute a trade at the current market rate (oracle price) instantly with regular exchange fees. Next Price Orders offer a substantial reduction in exchange fees by executing your order at the next, future price update.

![](https://mirror.xyz/\_next/image?url=https%3A%2F%2Fimages.mirror-media.xyz%2Fpublication-images%2FPMtoKnkICS3aycJtmohBO.png\&w=3840\&q=90)

Once you’ve toggled to Next-Price you won’t notice a huge change on the order entry panel, but rest assured as long as Next-Price is selected orders will be placed accordingly and traders can submit trades as they normally would.​

![A next price order shown in the Open Orders tab](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MigG4JjHTDtxrb2SknW%2Fuploads%2FuqxJqoubXxulvqXt6WlE%2F3.png?alt=media\&token=9649ae2b-caf8-426e-b69e-7f2ede709c03)

When the order is executed by a Keeper, it disappears from the Open Order tab and will show as usual on the Open Position tab.

![](../../../.gitbook/assets/Screen\_Shot\_2022-04-28\_at\_8.32.07\_PM.png)

{% hint style="danger" %}
Note that the Keeper fee will be refunded if cancelled manually, but the commitment fee will be forfeited when traders cancel their next price order.
{% endhint %}

Once submitted traders will see their pending next price order in the Open Orders tab along with its relevant information. Here traders can cancel their next price order in case they need to. At the next oracle update, an Execute button appears here where traders have the chance to manually execute their order. However, in reality the order will most likely be picked up within milliseconds by a Keeper, so we advise you to simply check after a few seconds if the order is executed.

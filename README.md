# Smart Contract Security Portfolio
> Vulnerability writeups, competitive audit reports (CodeHawks/Cantina), and reproducible security tests.

## Findings

Judged-valid findings only.

1. CodeHawks · First Flight

| Sev | Finding | Report|
| --- | --- | --- |
| High |mintSnowman lacks access control; anyone can mint without limit, effectively bypassing the airdrop system and rendering the entire airdrop invalid | [Report](https://codehawks.cyfrin.io/c/ai-snowman-merkle-airdrop-cmjaukcg70000l10407x9qxci/s/1) |
| High | MESSAGE_TYPEHASH does not strictly follow the EIP-712 standard types| [Report](https://codehawks.cyfrin.io/c/ai-snowman-merkle-airdrop-cmjaukcg70000l10407x9qxci/s/5)|
| High |After the user clicked "like" and transferred ETH to the contract, it was not recorded in userBalances.| [Report](https://codehawks.cyfrin.io/c/ai-datingdapp-cmjaukcg70000l10407x9qxci/s/1)|
| High | The upgraded contract defines a different storage layout for state variables, which conflicts with the layout of the older contract version.| [Report](https://codehawks.cyfrin.io/c/thunder-loan-cmjaukcg70000l10407x9qxci/s/1)|
| High |Erroneous updateExchangeRate() call in deposit() inflates exchange rate without real fee income| [Report](https://codehawks.cyfrin.io/c/thunder-loan-cmjaukcg70000l10407x9qxci/s/2)|
| High |It is possible to use someone else's account to buy NFTs for oneself.| [Report](https://codehawks.cyfrin.io/c/ai-santas-list-cmjaukcg70000l10407x9qxci/s/1)|
| High |The checklist does not enforce permissions according to business requirements and affecting normal business operations| [Report](https://codehawks.cyfrin.io/c/ai-santas-list-cmjaukcg70000l10407x9qxci/s/3)|
| High |Determining whether a user has already claimed a gift by checking their balance is flawed: an attacker could first claim the gift and then transfer away the balance, allowing repeated claims.| [Report](https://codehawks.cyfrin.io/c/ai-santas-list-cmjaukcg70000l10407x9qxci/s/4)|
| High |The refund function is vulnerable to reentrancy attacks.| [Report](https://codehawks.cyfrin.io/c/ai-puppy-raffle-cmjaukcg70000l10407x9qxci/s/2)|
| High |When refunding a user, only the user's address is changed to the zero address, but the players count is not updated, which can cause the zero address to appear as a winner in a draw or cause incorrect fund calculations.| [Report](https://codehawks.cyfrin.io/c/ai-puppy-raffle-cmjaukcg70000l10407x9qxci/s/3)|
| High |totalFees is stored as UINT64. If the value of entranceFee is too large, a smaller number of users can cause totalFees to overflow, resulting in loss of funds.| [Report](https://codehawks.cyfrin.io/c/ai-puppy-raffle-cmjaukcg70000l10407x9qxci/s/4)|
| High |Users can claim airdrop rewards repeatedly.| [Report](https://codehawks.cyfrin.io/c/ai-airdropper-cmjaukcg70000l10407x9qxci/s/1)|
| High |An attacker can steal the nftDealers contract’s balance via collectUsdcFromSelling(), draining it until the balance is zero or nearly zero| [Report](https://codehawks.cyfrin.io/c/2026-03-nft-dealers/s/69)|
| Medium |The business requirement was to spend 2e18 to purchase the NFT, but the burn only destroyed 1e18, which seriously contradicts the business description and resulted in loss of profit funds.| [Report](https://codehawks.cyfrin.io/c/ai-santas-list-cmjaukcg70000l10407x9qxci/s/2)|
| Medium |During withdrawal operations in `withdrawFees`, an attacker can use the `selfdestruct` mechanism to modify `address(this).balance`, causing the `require` condition to always fail and preventing funds from ever being withdrawn.| [Report](https://codehawks.cyfrin.io/c/ai-puppy-raffle-cmjaukcg70000l10407x9qxci/s/1)|
| Medium |In enterRaffle, when the array is very large, the algorithm for checking duplicate players is O(n^2), which can lead to excessively high gas and transaction failure.| [Report](https://codehawks.cyfrin.io/c/ai-puppy-raffle-cmjaukcg70000l10407x9qxci/s/5)|
| Medium |Non-whitelisted users cannot list items for sale after purchase; this does not match the business description.| [Report](https://codehawks.cyfrin.io/c/2026-03-nft-dealers/s/71)|
| Low |As long as someone calls the earnSnow function within the specified time, the global timer s_earnTimer is refreshed, and no one else can call it for one week.| [Report](https://codehawks.cyfrin.io/c/ai-snowman-merkle-airdrop-cmjaukcg70000l10407x9qxci/s/2)|
| Low |In buySnow, any purchase resets the global timer s_earnTimer, preventing other users from using the free earnSnow function for a week.| [Report](https://codehawks.cyfrin.io/c/ai-snowman-merkle-airdrop-cmjaukcg70000l10407x9qxci/s/3)|
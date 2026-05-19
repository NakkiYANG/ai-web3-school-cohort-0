# Day 1 — Scope & report format

我今天学习了关于 NFT 安全审计的一点知识。

---

## Title
Missing reentrancy protection in `mint()` allows unlimited NFT minting

## Severity
High

## Evidence
SimpleNFT.sol lines 42–48

```solidity
function mint(address to) public payable {
    require(msg.value >= 0.1 ether, "Insufficient payment");
    require(totalSupply() < MAX_SUPPLY, "Sold out");

    _safeMint(to, totalSupply() + 1);
    // State updates and refund logic occur after minting,
    // which is an external call at this point.
}
```

## Explanation
The function uses `_safeMint`, which makes an external call to the recipient's `onERC721Received` hook if the recipient is a contract.

During this callback, the contract’s state (e.g., the actual minted count) has not yet been updated. An attacker can re-enter the `mint` function and mint additional tokens within the same transaction.

## Impact
- An attacker can mint an arbitrary number of NFTs beyond the `MAX_SUPPLY` cap in a single transaction.
- The expected scarcity and economic model of the collection are completely broken, driving the NFT value to zero.
- The attacker only pays the minimum mint price once while receiving multiple NFTs, causing direct financial loss to the project.

## Recommendation / Fix
1. Follow the **checks-effects-interactions** pattern: update all state variables (e.g., increment `_nextTokenId`) before calling `_safeMint`.
2. Alternatively, add a reentrancy guard to the `mint` function (e.g., using OpenZeppelin's `ReentrancyGuard`).
3. Prefer `_mint` over `_safeMint` when the recipient is known to be an EOA or when callbacks are handled separately, to avoid external calls during state changes.

## Fixed code example
```solidity
function mint(address to) public payable nonReentrant {
    require(msg.value >= 0.1 ether, "Insufficient payment");
    require(totalSupply() < MAX_SUPPLY, "Sold out");

    uint256 tokenId = totalSupply() + 1;
    _safeMint(to, tokenId);
}
```

## Reference
- SWC-107
- Ethernaut Level 10 "Re-entrancy"

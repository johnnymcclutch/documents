# Joltify Chain Bridge

To allow the token transfer from and to one public chain (for example, Ethereum chain or Binance smart chain) to Joltify chain, cross chain bridge are employed to allow users to send and receive the token in bi-direction.



### Transferring Token From Public Chain To  Joltify Chain

1. User Alice transfers her token to the bridge router on the public chain end.
2. Once Joltify chain validator observes the transfer to the given bridge router end, it will mint the corresponding amount of wrap-tokens to the user’s corresponding Joltify chain address.&#x20;

### Transferring Token From Joltify Chain To Public Chain

1. User Bob transfers his token to the bridge router on the Joltify chain end.
2. Once Joltify chain validator observes the transfer to the given bridge router end, it will transfer the corresponding token to Bob address on the public chain.
3. Once the transfer transaction is confirmed on the public chain, the wrap token minted in Joltify chain will be burned.

### &#x20;Bridging Transaction  Verification and Signing

&#x20;The security of the Joltify bridge has the highest priority as it holds the liquidity of both ends. To avoid any validator cheat in the system by sending illegal transactions, we apply the TSS to ask a certain amount of validators  to sign on the outbound transactions. Since the majority of the nodes in the network are honest, it is impossible for the attackers to sign on the outbound transactions without the permission from the majority.

The following figure shows how the validators signing on one out-bound transaction.

1. Different validators monitor the Joltify chain bridge router independently. Once they see a transaction coming to the Joltify chain bridge router, they will verify the correctness of the transaction.
2. If the transaction is invalid, they will drop the transaction, otherwise, they will start a Tss signature generation rounds with other validators on the corresponding transaction.
3. Other validators will participant in the signature generation as well, and finally, all the validator will get the signature of the corresponding transaction and put the corresponding transaction on Joltify Chain.
4. If the transaction is the inbound transaction, the equivalent token will be minted on Joltify chain. If it is the outbound transaction, the token will be transferred to the user's wallet with the approval of the validators.

![Validators Sign On Transactions](../../.gitbook/assets/signature.png)

### &#x20;

&#x20;
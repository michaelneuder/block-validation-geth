[original readme](README.original.md)

geth validation: 
allows two types of validator payments:
1) increase in coinbase balance from state transition
2) explicit last txn paid directly to validator address. 

from relayooor fork: https://github.com/relayooor/go-ethereum

Introduces method `flashbots_validateBuilderSubmissionV1` which validates increase in coinbase balance for all block submissions.

This is just a clone of [flashbot's validation](https://github.com/flashbots/block-validation-geth) with tracing/blacklisting removed as it's rather slow and unnecessary.

Logic allows to send to pay block reward via last transaction or directly via `coinbase` with belief that privacy is more important than edge case such approach produces.

from flashbots fork: https://github.com/flashbots/block-validation-geth

Geth with additional RPC method `flashbots_validateBuilderSubmissionV1`.  
The new method accepts `github.com/flashbots/go-boost-utils/types.BuilderSubmitBlockRequest` - boost relay builders' block submission.  
It will ensure that the block is valid and that it transfers the expected funds to the fee recipient.  

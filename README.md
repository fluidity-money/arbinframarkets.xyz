


# ARB Infra Markets

ARB Infra Markets is a simple permissionless commit/reveal natural language oracle,
powered by USDC and Staked ARB, built with Arbitrum Stylus. It is primarily used by
[9lives](https://9lives.so), deployed on [Superposition](https://superposition.so) and
Arbitrum One.

```mermaid
sequenceDiagram
    Created ->> Called: call()
    alt Is "whinged" within two days
        Called ->> Whinged: whinge()
        loop Is within two days
            Whinged ->> Committed: predict()
            Committed ->> Revealed: revealed()
        end
        opt After two days
            Whinged ->> Declared: declare()
        end
        loop For each bad bettor
            Declared ->> Sweeping: sweep()
        end
    else Passes two days
        Called ->> Closed: closed()
    end
    Closed ->> Receiver: Calls declare
    Declared ->> Receiver: Calls declare
```

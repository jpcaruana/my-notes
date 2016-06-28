# The wonderful world of webhooks

    Lorna Mitchell @lornajane
    slides: https://speakerdeck.com/lornajane/the-wonderful-world-of-webhooks
    10 minute talk

Webhooks are everywhere (slack, github, ...). It is all about **moving** data.

With regular API, the client spends a lot of time asking the server about data change. It is expensive. With webhooks, the server has to know where to send its data. It is like **pub/sub over HTTP**.

Payload should be verbose to avoid creating your own DDOS attack (clients calling other URLs to have more detailled data)

How to receive a webhook:

- store / close connexion
- ack
- process (use a queue)

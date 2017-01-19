Dependencies and Contracts
---

Yesterday during my group lunch, we talked about dependencies management in IoT and application evolution.
One comment made by XXX was: what if gravity becomes open-sourced? That leads to the thought in this blog.

To evolve or not to evolve

1. Stale application considered bad.
2. Upgrading without notice is quirky
3. Testing is not sufficient
4. Shit happens

Contracts are easy to made, hard to maintain. We make assumptions all the time.
Worse, people are not aware of the existence of such contracts; only judging with one observation of the results.

Gravity, law of physics are like contracts that mechanical engineers made.
But software is mostly artifacts, in an ideal world of computation you can do anything.

Scanning and testing?
https://www.ftc.gov/iot-home-inspector-challenge

Contracts with a company? Or startup? Startups gone, subscription service?

Rust and Go.
Rust has a deep learning curve, a.k.a. barrier to entry. The libraries created are mostly stable.
I've encountered little issue (was having trouble with `syntex` and a couple of compiler plugins before 1.15 macros 1.1)

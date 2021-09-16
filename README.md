# tantivy-wasm

# this repo is a fork where I (@bakkot) am attempting to get [phiresky's repo running](https://github.com/phiresky/tantivy-wasm).

Steps, starting from the original repo:

- ensure you have `node`, `yarn`, and `cargo` set up
- make a directory to hold all the stuff. in that directory:
- clone https://github.com/phiresky/tantivy-wasm
  - I did this at commit 0990c5ffcb1ec40eb58f0821dbb20a0f517bb44e
- clone https://github.com/phiresky/tantivy
  - I did this at commit 6bd8a8d9ef702bda9b76119c2732542a8aa3e04e
- clone https://github.com/phiresky/tantivy-fst
  - I did this at commit edfdf0a78ed4a27d270dd8d898a3d50c046bfc7b
- `cd tantivy-wasm`; all future commands are relative to that directory
- reproduce the indices used in the demo. there's no instructions for this, so I just downloaded the wikipedia index files from [the running demo](https://demo.phiresky.xyz/tmp-ytccrzsovkcjoylr/dist/index.html).
- `yarn && yarn build`

In principle, I believe it should work at this point if you run a webserver which supports range requests in the `tantivy-wasm` directory. Alas, no. Running `npx http-server` and opening the demo does work, and it makes a few requests, but it gets to the `bf92c5e40ac948299bc68912773ab04f.store` request and then hangs - that request shows up as pending in the dev tools and the browser thread for the worker is permanently stuck at 100% CPU utilization until you kill it.

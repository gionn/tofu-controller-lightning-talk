# Evolution, not revolution

Slides for a 15-minute lightning talk at [ContainerDay](https://www.containerday.it/) on running existing Terraform inside Kubernetes GitOps with [tofu-controller](https://github.com/flux-iac/tofu-controller), instead of rewriting it.

The talk covers the Terraform custom resource, writing outputs to Secrets, ordering stacks and apps with `dependsOn`, approving plans through Git, drift detection, and the trade-offs.

Read the slides in [tofu-controller-lightning-talk.pdf](./tofu-controller-lightning-talk.pdf), or run the deck locally with [Slidev](https://sli.dev):

```sh
npm install
npm run dev
```

The dev server opens the deck at http://localhost:3030. Speaker notes are in the trailing HTML comment on each slide in `slides.md`.

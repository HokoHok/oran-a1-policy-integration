# Recorded evidence and its limits

These are historical records from the author's HackMD notes. They were reviewed during portfolio preparation, but the old Kubernetes stack was not restarted or tested again.

| Release | Record | What it supports | Limit |
| --- | --- | --- | --- |
| J | [Near-RT RIC pod snapshot](../evidence/j-near-rt-ric-pods.png) | A1 Mediator, E2 components, and most displayed platform pods were `Running` when captured. | It is a point-in-time pod listing, not a current health check. |
| J | [Non-RT RIC pod snapshot](../evidence/j-non-rt-ric-pods.png) | PMS and several Non-RT RIC components were `Running`. | The same screenshot shows a `CrashLoopBackOff` participant and Kong components that were not ready. |
| J | [J-release HackMD notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/S1Dij0ABR) | The notes record PMS `/a1-policy/v2/rics` returning `a1mediator` as `AVAILABLE`, A1 policy type listing `[20008]`, and a registered `service1`. | The notes do not show a J-release policy instance delivered to a Traffic Steering xApp. |
| F | [Policy control panel screenshot](../evidence/f-policy-instance.png) | Policy type `20008` had instance `1000`, targeted at `ric3`, in the earlier F-release experiment. | It is evidence for F-release only. |

The [F-release Near-RT RIC setup notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/HJbMQEgYn) and [F-release connection notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/BkkQb8UWA) document additional installation and Traffic Steering xApp steps. The [RAN PM/rApp notes](https://hackmd.io/@_Rheq0BSRpaANOaleSyL2Q/HkeIBWmvC) document a later extension; they explicitly defer part of the PM connection procedure. Neither sequence is presented here as proof of a complete J-release end-to-end control loop.

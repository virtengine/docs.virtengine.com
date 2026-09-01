---
title: Network Launch Schedule
order: 2
---

## Launch windows

| Network | Launch window | Role |
| --- | --- | --- |
| **TestNet** | **January 2027** | Public pre-production validation and operator rehearsal. |
| **MainNet** | **March 2027** | Persistent production launch after TestNet exit criteria and a separate go/no-go approval. |

These are month-level windows. Exact UTC dates and times will be published
through the formal launch process. Neither network should be described as live
until an official launch confirmation is published.

## TestNet versus MainNet

TestNet is the public proving environment. Validators, providers, integrators,
and application teams use it to test consensus, upgrades, VEID, marketplace
and settlement flows, monitoring, recovery, and incident response. TestNet may
be reset, its tokens have no production value, and its data or balances are
not guaranteed to carry into MainNet.

MainNet is the production network. It uses approved release artifacts,
canonical genesis inputs, and production economic parameters. Its state is
intended to persist, so it requires final artifact verification and a fresh,
explicit production `GO` decision.

## Why the windows are separated

January provides real multi-operator TestNet evidence. February is reserved
for observing results, fixing and re-testing defects, completing security and
operational reviews, freezing production artifacts, and coordinating the
validator set. March is the MainNet window only after those exit criteria are
accepted.

This separation prevents TestNet rehearsal evidence from being mistaken for
production approval and reduces the risk of carrying unresolved consensus,
security, economic, integration, or operational issues into persistent
MainNet state.

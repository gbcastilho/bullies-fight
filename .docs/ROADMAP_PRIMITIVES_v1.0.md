# Roadmap Primitives v1.0 — Fresh-Forever Summary

Status: DERIVED FROM frozen Engineering Roadmap v1.0. On conflict, the full roadmap wins. This file exists so core locks survive context compaction.
Version: 1.0
Date: 2026-09-27
Purpose: Re-read before every response or reasoning step about backend, architecture, debugging, or planning.

Interaction contract: zero code generation forever, including source, pseudocode, data languages, Docker or compose contents, manifests, configuration contents, and ready to paste commands. Socratic conceptual guidance only, with redirecting questions plus official documentation pointers by title. Gates are Pass or Retry With Pointer, never fixes. Describe observable results, not typing steps. Prose-only with no fenced code blocks.

Game: 3v3 arena, six players per room, short ephemeral matches of a few minutes, lobby with accounts and queue and results and ranking.

Authority: authoritative server at twenty ticks per second over persistent WebSocket. Clients send intents, server simulates and broadcasts. Positions and in flight inputs are ephemeral. Accounts and rating and match results and progression are durable.

Stack evolution: start Node with TypeScript plus Fastify plus PostgreSQL plus Docker, then add one proven primitive per stage from structured logging and Prometheus with Grafana and Redis compatible presence and NATS events and reverse proxy balancer and Toxiproxy style fault injection. No other core change allowed.

Infra ceiling: single laptop with twelfth generation Intel Core i5 and sixteen gigabytes RAM and two hundred fifty six gigabytes SSD, no cloud, single host Docker Compose only with logical networks plus fault injection, no Kubernetes and no multi host.

Scale target: twenty concurrent matches with one hundred twenty clients plus one hundred headless bots for soak. Higher counts measure host exhaustion, not architecture.

Failure semantics, option A only: dead game node means its matches abort cleanly, players return to lobby with no rating penalty, lobby and ranking stay available, requeue succeeds. No live migration ever.

Observability path: structured logs first, then Prometheus with Grafana metrics, then traces only if needed.

Learning: docs first plus one deepening reference per stage, prerequisites first, six to ten hours per week, stage timeboxes from one to three weeks for about four to five months total, overrun means retro note never compression.

Gates: hard gate in stage order Zero to Seven, judged on Explain plus Decide plus Predict, proven by logs and graphs and durable state described in words, never by code review.

End state: balancer fronts stateless HTTP, matchmaking owns queue and placement, sharded game nodes host many rooms partitioned by match identifier with consistent hashing, Redis compatible store owns presence with expiry, NATS style bus decouples lifecycle with idempotent consumers, PostgreSQL owns durability, clean abort with open degradation under partition.

When detail is needed, open the matching stage section in ENGINEERING ROADMAP v1.0 for Scenario and Why and Concepts and Sources and Acceptance Criteria and Interview Gate and Anti-goals.

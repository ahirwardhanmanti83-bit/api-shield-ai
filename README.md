# API-Shield AI 🛡️

> **Zero-Overhead Edge Circuit Breaker & Real-Time Token Runaway Cost Protection for LLM Deployments (GPT-4o, Claude 3.5 Sonnet, Gemini 1.5, DeepSeek).**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Edge Engine](https://img.shields.io/badge/Edge%20Engine-Active-brightgreen.svg)]()
[![Server Cost](https://img.shields.io/badge/Server%20Cost-%240.00-blue.svg)]()

---

## ⚡ Access the Live Edge Shield

👉 **[Launch API-Shield AI Web Application](https://ahirwardhanmanti83-bit.github.io/api-shield-ai/)**

---

## 🎯 The Core Problem

LLM engineering teams face catastrophic runaway API billing spikes due to:
- Recursive agent execution loops.
- Client-side token abuse and unthrottled prompt injections.
- Massive uncompressed payload loops.

Traditional gateways (Portkey, Helicone) charge recurring platform fees and add network latency. **API-Shield AI executes client-side and edge-native token bucket circuit breaking with ZERO server overhead.**

---

## 🚀 Key Architectural Features

- **Real-Time Runaway Cost Modeling:** Live exposure index measuring dollar burn across Claude 3.5 Sonnet, GPT-4o, Gemini 1.5 Pro/Flash, and DeepSeek-V3.
- **Client-Side Air-Gapped Telemetry:** Zero external database dependencies; privacy-first session telemetry.
- **Hardware Circuit Breaker:** Pre-armed $100 emergency hard-stop logic.
- **Edge Deployment Ready:** Drop-in Cloudflare Worker / Vercel Edge middleware implementation.
- **Instant Monetization Rails:** Direct $2 edge template unlock and enterprise access.

---

## 🛠️ Quick Edge Integration

```javascript
// Drop-in Edge Token Circuit Breaker
import { createCircuitBreaker } from './api-shield-edge.js';

export default {
  async fetch(request, env) {
    const shield = createCircuitBreaker({ hardCapUSD: 100 });
    const allowed = await shield.verify(request);
    
    if (!allowed) {
      return new Response(JSON.stringify({ error: "API-Shield: Budget circuit broken" }), { status: 429 });
    }
    return fetch(request);
  }
};

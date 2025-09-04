# 🚫 SIMD-Free Patch for `reed-solomon-erasure`

This is a **custom fork** of [`reed-solomon-erasure`](https://github.com/darrenldl/reed-solomon-erasure) designed to allow [`jito-labs/shredstream-proxy`](https://github.com/jito-labs/shredstream-proxy) to compile and run on **non-SIMD-capable CPUs**.

---

### 🔧 What This Patch Does

- **Disables all SIMD-accelerated logic**, even when the `simd-accel` feature is required (e.g., by `solana-ledger`)
- **Re-routes `#[cfg(feature = "std")]` blocks** to be triggered by the `simd-accel` flag
- Avoids unsafe C bindings that would fail on CPUs without proper SIMD support

---

### ⚠️ Notes

- This fork is only meant as a compatibility shim.
- Do not use it for production or performance-sensitive workloads.
- If upstream crates drop or change their feature requirements, this may break.

---

### ✅ Purpose

> To make `shredstream-proxy` buildable and testable on machines that **do not support AVX, NEON, or other SIMD instructions**.

---

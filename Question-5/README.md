# Problem 5 — Received Power and Threshold Exceedance Probability

## Overview

This project provides a clean and self-contained implementation of **Problem 5** from the laboratory assignment.

The objective is to evaluate the received signal power at a distance of **2 km** and determine the probability that the received power exceeds a specified threshold.

The analysis uses:

- A fitted Close-In (CI) path-loss model
- A transmit power of 100 W
- A query distance of 2000 m (2 km)
- An estimated shadowing standard deviation
- A Gaussian shadowing model
- A received-power threshold of -95 dBm

---

## Objective

The main objectives are to:

1. Calculate the path loss at a distance of 2 km.
2. Determine the mean received signal power.
3. Model shadowing as a Gaussian random variable.
4. Calculate the probability that the received power exceeds -95 dBm.

---

## Mathematical Model

### 1. Close-In (CI) Path-Loss Model

The path loss is modeled as:

$$
PL(d) =
FSPL(d_0)
+
10n\log_{10}\left(\frac{d}{d_0}\right)
+
X_\sigma
$$

where:

- $PL(d)$ — path loss at distance $d$, in dB
- $FSPL(d_0)$ — free-space path loss at the reference distance
- $n$ — path-loss exponent
- $d$ — transmitter-receiver separation distance
- $d_0$ — reference distance
- $X_\sigma$ — shadowing component
- $\sigma$ — standard deviation of the shadowing component

For the laboratory scenario:

Carrier frequency : 3.5 GHz
Reference distance : 1 m
Speed of light : 3 × 10^8 m/s
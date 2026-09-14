 Objective

Evaluates the received signal power at a distance of 2 km and determines the probability that the received power exceeds a specified threshold.

The analysis uses:
A fitted close-in (CI) path-loss model.
A transmit power of 100 W.
A query distance of 2000 m (2 km).
An estimated shadowing standard deviation.
A Gaussian shadowing model to calculate the probability that received power is greater than −95 dBm.





Mathematical Model

Close-In Path-Loss Model
The path loss is represented as

[
PL(d) = FSPL(d_0) + 10n\log_{10}\left(\frac{d}{d_0}\right) + X_\sigma
]

where:

(PL(d)) = path loss at distance (d), in dB

(FSPL(d_0)) = free-space path loss at the reference distance

(n) = path-loss exponent

(d_0) = reference distance

(X_\sigma) = shadowing component

(\sigma) = standard deviation of the shadowing component

For the lab scenario:
Carrier frequency: 3.5 GHz

Reference distance: 1 m

Speed of light: (3\times10^8) m/s

The theoretical free-space path loss is

20\log_{10}
\left(
\frac{4\pi d_0 f_c}{c}
\right)
]

3.2 Received Power

The transmit power is converted from watts to dBm using

10\log_{10}(P_t[\mathrm{mW}])
]

The mean received power is then calculated as

P_t[\mathrm{dBm}] - PL(d)
]

For (P_t=100) W,

[
P_t = 50\ \mathrm{dBm}
]

3.3 Probability of Exceeding the Threshold

The received power is modeled as a Gaussian random variable:

[
P_r \sim \mathcal{N}(\mu_{P_r},\sigma^2)
]

For the threshold (P_{\mathrm{th}}=-95) dBm, the standardized value is

[
z =
\frac{P_{\mathrm{th}}-\mu_{P_r}}{\sigma}
]

Therefore,

1-\Phi(z)
]

where (\Phi(z)) is the standard normal cumulative distribution function.

The implementation evaluates this probability using the survival function provided by scipy.stats.

4. Data Handling

The program first looks for:

pathloss.txt

in the current working directory.

If pathloss.txt is available

The program loads the measurement data directly. The expected format is:

distance_in_meters    path_loss_in_dB

with at least two columns.

If pathloss.txt is not available

The program automatically generates a documented synthetic path-loss dataset using the same CI model. This fallback allows the script to remain executable on a fresh machine without requiring the measurement file.

When the real measurement file is present, it is used automatically.


T









Expected Analysis Output

When the original pathloss.txt measurement data is used, the analysis is expected to produce values consistent with the notebook results, including approximately:

Transmit power       : 100 W
Transmit power       : 50.000 dBm
Distance              : 2000 m
Path loss             : 145.742 dB
Mean received power  : -95.742 dBm
Shadowing std. dev.  : 3.32 dB
Probability           : approximately 41.17%

Small differences in the final digits may occur if the input data or numerical environment differs.
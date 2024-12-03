# Performance Analysis: Autoencoder vs FFT

![Metrics](https://github.com/user-attachments/assets/6d020ed0-fe3d-4c4b-a31f-c4cc9d752885)

## Overview
This analysis compares the performance of Autoencoder and FFT methods across different window sizes (300k to 50M) and reduction rates (100x, 300x, 1000x) using four key metrics.

## Error Metrics Analysis

### Mean Squared Error (MSE)
- **Autoencoder**:
 - Shows higher error rates compared to FFT
 - Error decreases with larger window sizes
 - Higher reduction rates (1000x) result in larger errors
 - 100x reduction maintains lowest error across all window sizes

- **FFT**:
 - Consistently lower error rates than Autoencoder
 - More stable performance across window sizes
 - Maintains better error rates even at high reduction rates
 - Shows clear advantage in accuracy over Autoencoder

### Mean Absolute Error (MAE)
- Similar patterns to MSE
- FFT maintains significantly lower MAE across all configurations
- Autoencoder shows improvement with larger windows but still higher error rates
- Error increases with higher reduction rates for both methods

## Statistical Measures

### Pearson Correlation
- **Autoencoder**:
 - Strong correlation (>0.95) for 100x reduction
 - Performance degrades significantly with higher reduction rates
 - Correlation decreases with larger window sizes
 - 1000x reduction shows poorest performance (~0.6-0.7)

- **FFT**:
 - Excellent correlation (>0.95) across all configurations
 - Very stable performance regardless of window size
 - Minimal impact from different reduction rates
 - Maintains high correlation even at 1000x reduction

### R-squared Score
- **Autoencoder**:
 - Shows similar patterns to Pearson correlation
 - Best performance with 100x reduction (~0.95-0.98)
 - Significant degradation at higher reduction rates
 - Largest windows show poorest performance

- **FFT**:
 - Consistently high R-squared values (>0.95)
 - Minimal variation across window sizes
 - Maintains performance even at high reduction rates
 - Shows superior stability compared to Autoencoder

## Key Findings
1. FFT consistently outperforms Autoencoder across all metrics
2. Autoencoder performance is more sensitive to both window size and reduction rate
3. Higher reduction rates (1000x) significantly impact Autoencoder performance while FFT remains stable
4. FFT maintains high statistical correlation even with aggressive data reduction
5. Larger window sizes tend to negatively impact Autoencoder performance more than FFT

## Conclusion
FFT demonstrates superior and more stable performance across all tested configurations, making it the more reliable choice for data reduction tasks. While Autoencoder can achieve good results with lower reduction rates and smaller windows, its performance degrades more significantly with larger windows and higher reduction rates.

# Execution Time Analysis: Autoencoder vs FFT

![Execution_time](https://github.com/user-attachments/assets/a67f4bab-a0b6-481a-ab2e-10aba3aa63ce)


## General Trend
- Both Autoencoder and FFT show increasing execution times as the window size grows
- The relationship appears roughly logarithmic (note the log scale on y-axis)
- The increase becomes more pronounced after the 1M window size

## Method Comparison
- FFT (solid lines) is generally faster than Autoencoder (dashed lines), especially for smaller window sizes
- The difference is most noticeable in the 300k-1M range
- The gap narrows somewhat at larger window sizes (10M-50M)

## Reduction Rate Impact

### FFT Performance (Orange/Solid Lines)
- Different reduction rates (100x, 300x, 1000x) have minimal impact on execution time
- The lines are very close together, suggesting the reduction rate doesn't significantly affect processing time

### Autoencoder Performance (Blue/Dashed Lines)
- Shows more variation between reduction rates
- Lower reduction rates (e.g., 100x) tend to require more processing time due to preserving more data
- The difference becomes more pronounced at larger window sizes
- This is expected as maintaining more detailed information (100x reduction) requires more computational effort than aggressive reduction (1000x)

## Scalability
- FFT shows more predictable, linear scaling in log space
- Autoencoder shows slightly more erratic scaling, particularly at larger window sizes
- Both methods show significant time increases from 10M to 50M window sizes

### Key Takeaway
FFT demonstrates more consistent performance across different reduction rates, making it potentially more suitable for time-critical applications. The Autoencoder's execution time is more sensitive to both window size and reduction rate, with lower reduction rates requiring notably more processing time due to the need to preserve more detailed information in the compressed representation.

# Chromosome scale
## 100X Reduction Ratio
![Chrom_100x](https://github.com/user-attachments/assets/7fdf9ca1-24c6-4089-8595-b0ed01246226)


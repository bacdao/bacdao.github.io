# Execution Time Analysis: Autoencoder vs FFT

![Execution time comparison between Autoencoder and FFT](https://github.com/user-attachments/assets/1c783bd4-5998-49f1-ba42-aefb59885c04)

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

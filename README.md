Pulse-Code-Modulation
Aim:

To implement Pulse Code Modulation (PCM) for encoding and decoding a sinusoidal signal using quantization and to observe the output waveforms.

Tools/Software Required:

Python Software
-> Numpy Library

-> Matplotlib Library

-> Scipy Library (for signal processing

Program:

import numpy as np

sampling_rate = 5000 # Sampling rate (samples per second)

frequency = 50 # Frequency of the message signal (analog signal)

duration = 0.1 # Duration of the signal in seconds

quantization_levels = 16 # Number of quantization levels (PCM resolution)

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t)) # Increased clock frequency to 200 Hz

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels

quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step

pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)

plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')

plt.title("Message Signal (Analog)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 2)

plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')

plt.title("Clock Signal (Increased Frequency)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 3)

plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')

plt.title("PCM Modulated Signal (Quantized)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 4)

plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')

plt.title("Signal Without Demodulation")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.tight_layout()

plt.show()

Output Waveform:

![WhatsApp Image 2025-03-27 at 20 19 27_f4b5a287](https://github.com/user-attachments/assets/7fe543a8-0024-4c06-a44c-d0760a4b6631)

Results:

The PCM encoding process successfully quantized the original sine wave into 16 levels.

The demodulated signal closely resembled the original signal with minor quantization noise.

The output waveforms validated the functioning of PCM in digital communication systems.

EXP.NO.9-Simulation-of-Pulse-Code-Modulation

9.Simulation of PCM

AIM

To implement the simulation of pulse code modulation using python libraries.

SOFTWARE REQUIRED

Google colab (Python)
Numpy
Matplotlib

ALGORITHMS

Generate a sinusoidal signal using a high-resolution time vector.

Sample the sine wave at uniform intervals based on a chosen sampling frequency.

Round each sampled value to the nearest level from a fixed number of quantization levels.

Encode each quantized value into a binary format.

Decode the binary data back into quantized values.

Use decoded quantized values to recreate a step-wise version of the original signal.

Plot the original, sampled, quantized, and reconstructed signals

PROGRAM

import matplotlib.pyplot as plt

import numpy as np

sampling_rate = 5000

frequency = 50

duration = 0.1

quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

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

OUTPUT

![image](https://github.com/user-attachments/assets/490e71d8-a086-4530-aeed-89e03b3cf773)

RESULT / CONCLUSIONS

Thus the pulse code modulation converts an analog sine wave into a digital signal and the graph is obtained.


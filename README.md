# Pulse-Code-Modulation
# Aim
Write a simple Python program for the modulation and demodulation of PCM, and DM.
# Tools required
Google CO-LAB
# Program
import numpy as np
import matplotlib.pyplot as plt

# Signal parameters
fs, f, T = 5000, 20, 0.5
t = np.arange(0, T, 1/fs)
msg = np.sin(2*np.pi*f*t)

# -------- Clock Signal --------
clk = np.sign(np.sin(2*np.pi*100*t))

# -------- PCM --------
L = 16
step = (msg.max()-msg.min())/L
pcm = np.round(msg/step)*step
pcm_demod = pcm  # Ideal reconstruction

Program
# -------- Delta Modulation --------
delta = 0.05
dm = [0]
steps = []

for s in msg:
    step = delta if s > dm[-1] else -delta
    steps.append(step)
    dm.append(dm[-1] + step)

dm_demod = np.cumsum([0] + steps)

# -------- Plot --------
plt.figure(figsize=(10,10))

plt.subplot(611); plt.plot(t,msg); plt.title("Analog Signal"); plt.grid()
plt.subplot(612); plt.plot(t,clk); plt.title("Clock Signal"); plt.grid()
plt.subplot(613); plt.step(t,pcm); plt.title("PCM Signal"); plt.grid()
plt.subplot(614); plt.plot(t,pcm_demod,'r--'); plt.title("PCM Demodulated"); plt.grid()
plt.subplot(615); plt.step(t,dm[:-1]); plt.title("Delta Modulation"); plt.grid()
plt.subplot(616); plt.plot(t,dm_demod[:-1],'g--'); plt.title("DM Demodulation"); plt.grid()

plt.tight_layout()
plt.show()

# Output Waveform
<img width="511" height="506" alt="593038068-8b692a32-4c08-470e-8d31-8f71be7648d6" src="https://github.com/user-attachments/assets/fc25ce8c-4d95-4ebe-a17b-77d481cd777a" />

# Results
Thus, the python program for the modulation and demodulation of PCM, and DM has been executed and verified successfully.


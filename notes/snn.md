# Spiking Neural Network (SNN)

> "Not all neurons fire all the time — some wait for the right moment to spike."  
> — Understanding how the brain *really* computes.

---

An **SNN (Spiking Neural Network)** is a type of artificial deep learning for classification that uses **spikes as input instead of continuous values**.  
The key concept:  
> The signal is not a continuous value but a **discrete spike train over time**.

---

## SNN Simulation

To understand how SNNs work, we simulate them using the **Leaky Integrate-and-Fire (LIF)** neuron —  
the most common and computationally efficient model in large-scale SNNs.  

**Why LIF?**  
Because it's the simplest and ideal for initial conceptual studies.

![SNN LIF Animation](/assets/animations/snn_lif_animation.gif)
The animation above visualizes how SNNs process information through **time** and **event-based communication (spikes)** instead of continuous signals.

There are two figure sections:  
1. **Membrane Potential Line ($V$)**  
2. **Discrete Spike Impulses (Events)**  

---

### Membrane Potential Line ($V$)
A continuous line starting near a resting potential ($V_{rest}$).  
It represents the neuron's **"readiness" to fire**.

### Discrete Spike Impulses (Events)
Sharp vertical lines (spikes) appear when the membrane potential hits the **threshold ($V_{thresh}$)**.  
At that moment — the neuron fires!

---

## Two Core Dimensions of SNNs

SNNs differ from standard ANNs in two crucial ways: **Time** and **Rate**.

---

### 1. The Time Dimension — *"How it computes"*

Traditional ANN:
```math
Output = Activation(Weights × Input)
```
SNN:

>The decision unfolds over many time steps, requiring the neuron to remember its state ($V$) between steps.
The rising and falling potential line shows this evolving memory.


### 2. The Information Coding — "What it computes"

In rate coding (common for classification tasks like the Iris dataset):

- Training/Inference:
The neuron that fires the most spikes (highest frequency) during the simulation window wins.

- Decay Rate's Role:
The **decay** (leakage) controls how long a neuron "remembers."
A **fast decay** = **short memory** → reacts only to strong inputs.


>Key Takeaway:
An SNN neuron can communicate only by overflowing its internal "bucket."
> Strong, constant input → frequent (high-rate) spiking
>Sparse input → low-rate, occasional spikes

If this reminds you of the leaky bucket algorithm, you're right — they share the same intuition.

![Leaky Bucket](/assets/animations/leaky_bucket.png)



## SNN vs Other Model Architectures
Artificial Neural Networks have been the foundation of AI, known for their conventional approach where input data consists of real-valued numbers, suitable for tasks like image recognition.

| Aspect            | ANN                                                                                                                                 | RNN                                                                                                                         | SNN                                                                                                                                                   | CNN                        |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| Full Name         | Artificial Neural Network                                                                                                           | Recurrent Neural Network                                                                                                    | Spiking Neural Network                                                                                                                                | Convolution Neural Network |
| Information Flows | **Feedforward**: Data flows in one direction (Input → Hidden Layers → Output). No internal memory or loops. | **Recurrent Loop**: Has a hidden state (memory) that feeds back into the network, allowing it to process sequential inputs. | **Event-Driven Spikes**: Neurons only communicate when their internal potential reaches a threshold (a "spike"). Asynchronous and sparse computation. |                            |
| Data Type         | **Static Data**: Tabular data (rows/columns), simple classification/regression.                                                     | **Sequential Data**: Time-series, sensor readings, logs, speech, video frames.                                              | **Temporal/Sparse Data** and **Neuromorphic Hardware**. Real-time, low-power sensor data.                                                             |                            |
| Example Use Case  | **Network Fault Classification** (e.g., Is this log data a 'Hardware' or 'Software' fault?)                                         | **Traffic Forecasting** (e.g., Predicting bandwidth demand next hour). Channel Prediction (forecasting signal quality).     | **Edge AI/Low-Power RAN**: Real-time, energy-efficient processing on low-power devices (e.g., anomaly detection on a 5G small cell).                  |                            |


## Why are SNNs a Cutting-Edge Model?

SNNs bring us closer to how biological brains compute — asynchronously, sparsely, and efficiently. This makes them a cutting-edge area, especially for "edge computing" and "next-generation" low-power devices.

- **The Neuron**: Unlike ANNs/RNNs that use continuous values (like a voltage level), SNNs communicate using discrete, binary spikes (like a sudden pulse) when a membrane potential is reached.

- **Core Strength**: Extreme Energy Efficiency. Because neurons compute only when spikes occur,
SNNs are event-driven → perfect for edge devices and neuromorphic hardware.

- **Core Limitation — Maturity & Training**. SNN training is less mature and more complex,
often achieving lower accuracy compared to optimized ANNs/RNNs — but it's improving rapidly.


>In short:
SNNs are the bridge between biological inspiration and neuromorphic intelligence —
paving the way for the next era of low-power, event-driven computing.

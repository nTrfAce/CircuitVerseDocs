# Decoders and Plexers

> This guide will teach you how to use the decoders and plexers available on Circuitverse.

Contributing Authors: [@brahmakulkarni](https://github.com/brahmakulkarni)

## Multiplexer

A multiplexer is used to selectively pass only one of the inputs provided to it. This is done using a control signal. The number of inputs is always a power of 2. If there are N control bits, then there can be a maximum of 2^N inputs.

Consider a simple multiplexer that takes two single-bit inputs (T1 and T2), a single-bit control signal (S) and has an output (Out). This Type of multiplexer is known as a 2 to 1 multiplexer. The truth table is given below:

|    S    |   Out   |
|---------|---------|
|    0    |   T1    |
|    1    |   T2    |

<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/746" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

Using the property menu (as shown in the getting started section) we can pass multi-bit inputs and also increase or decrease the number of inputs that can be given to the multiplexer.

Here is an example where there are 4 three-bit inputs and a two-bit control signal or a 4 to 1 multiplexer. The truth table is given below:

|    S1   |    S0   |    Out    |
|---------|---------|-----------|
|    0    |    0    |    T1     |
|    0    |    1    |    T2     |
|    1    |    0    |    T3     |
|    1    |    1    |    T4     |
<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/747" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

## Demultiplexer

A demultiplexer takes an input and passes it to only one of outputs. This is done using a control signal. The number of outputs is always a power of 2. If there are N control bits, we can choose to pass the output to any one of the 2^N output lines.

Consider a simple demultiplexer that takes a single-bit input (T), a single-bit control signal (S) and two single-bit outputs (O1 and O2).This type of demultiplexer is called a 1 to 2 demultiplexer. The truth table is given below:

|    S    |    O1   |    O2   |
|---------|---------|---------|
|    0    |    T    |    0    |
|    1    |    0    |    T    |

Its live cicuit is embedded below:

<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/756" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

Using the property menu (as shown in the getting started section) we can pass multi-bit inputs and also increase or decrease the number of outputs by changing the number of bits we want the control signal to have.

Here is another example of demultiplexer where a 3-bit input is taken and a two-bit control signal or a 1 to 4 demultiplexer. The truth table is given below:

|    S1   |    S0   |    O1   |    O2   |    O3   |    O4   |   
|---------|---------|---------|---------|---------|---------|
|    0    |    0    |    T    |    0    |    0    |    0    |
|    0    |    1    |    0    |    T    |    0    |    0    |
|    1    |    0    |    0    |    0    |    T    |    0    |
|    1    |    1    |    0    |    0    |    0    |    T    |

Its live circuit is embedded below:

<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/757" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

## Bit-selector

A bit-selector's function is self-explanatory. It takes a single or multi-bit input and gives the bit we desire to isolate as output. This is done using a single or multi-bit select line. The select line value indicates the specific bit we wish to isolate. An added feature is the bit-selector shows the bit we want to isolate (as chosen using the select line) within it's body in decimal form.

Consider a bit selector with a four-bit input. Let each of its bits be addressed separately as T3, T2, T1, T0 (from most significant to least significant). Let it have a two-bit select line (S1 and S0) and a single-bit output (Out). The truth table is given below:

|    S1   |    S0   |   Out   |   
|---------|---------|---------|
|    0    |    0    |    T0   |
|    0    |    1    |    T1   |
|    1    |    0    |    T2   |
|    1    |    1    |    T3   |

Its live circuit is embedded below:

<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/758" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

## Most Significant Bit (MSB) Detector

The MSB detector gives as output the bit position of the most-significant-bit of the input. In other words, it tells us at which bit position the right-most one is located. An enable output is also provided to show if the MSB detector is active. The bit position of the MSB is also shown in decimal form within the body of the MSB detector.

Consider an MSB detector with a four-bit input. Its live circuit is embedded below:
<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/11988" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>


## Least Significant Bit (LSB) Detector

The LSB detector gives as output the bit position of the least-significant-bit of the input. In other words, it tells us at which bit position the left-most one is located. An enable output is also provided to show if the LSB detector is active. The bit position of the LSB is also shown in decimal form within the body of the LSB detector.

Consider an LSB detector with a four-bit input. Its live circuit is embedded below:
<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/11990" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

## Priority Encoder

The priority encoder provided by Circuitverse works in a similar fashion to the MSB detector (in practice it can work like the LSB detector also). There is a specific output based on the bit position of the MSB, irrespective of the lesser significant bits. If there are N outputs, there will be 2^N inputs. A 'Valid' output labeled V is provided to indicate that at least one input is 1. Valid 0 output means none of the inputs are 1. Read the binary value of the output(s) to determine the input number of the highest input which is active. An example use of this circuit element is to indicate if any interrupt is present to a system, and to provide the value of the highest priority interrupt which is asserted.

Consider a priority encoder with four single-bit inputs (T3, T2, T1 and T0 from most to least-significant bit) and two single-bit outputs (O2 and O1 from most to least-significant bit). The truth table is given below:

|   T3    |   T2    |   T1    |   T0    |    V    |   O2    |   O1    |
|---------|---------|---------|---------|---------|---------|---------|
|    0    |    0    |    0    |    0    |    0    |    0    |    0    |
|    0    |    0    |    0    |    1    |    1    |    0    |    0    |
|    0    |    0    |    1    |    X    |    1    |    0    |    1    |
|    0    |    1    |    X    |    X    |    1    |    1    |    0    |
|    1    |    X    |    X    |    X    |    1    |    1    |    1    |

Its live circuit is embedded below:
<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/762" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

## Decoder

The decoder with N input bits has 2^N output lines. Suppose the value of the input is X, the Xth output line is made high.

Consider a decoder with a single two-bit input (T1 and T0 from most to least-significant bit) and four single-bit output lines (O4, O3, O2 and O1 from most to least-significant bit). The truth table is given below:

|   T1    |   T0    |   O4    |   O3    |   O2    |   O1    |
|---------|---------|---------|---------|---------|---------|
|    0    |    0    |    0    |    0    |    0    |    1    |
|    0    |    1    |    0    |    0    |    1    |    0    |
|    1    |    0    |    0    |    1    |    0    |    0    |
|    1    |    1    |    1    |    0    |    0    |    0    |

Its live circuit is embedded below:

<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/763" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen> </iframe>

## Parity Generator & Parity Detector

These combinational circuits are used together to make data transmission error tolerant. Parity generator is used by the sender and parity detector is used by the receiver.

### Parity Generator

Parity generator is used to generate a parity bit which is later used by parity detectors to detect errors in data transmission. The parity bit is added to the original message to be sent.

In an **even parity** generator, if the input message has even number of `1`s, the parity bit will be 0. On the other hand, if there are odd number of `1`s, parity bit generated will be 1.

#### Truth Table for an Even Parity Generator for a 3-bit word


| A  | B  | C  |  PARITY BIT(P)    |
|:-:|:-:|:-:|:-:|:-:|
|  0 |  0 |  0 |   0   |
|  0 |  0 |  1 |   1   |
|  0 |  1 |  0 |   1   |
|  0 |  1 |  1 |   0   |
|  1 |  0 |  0 |   1   |
|  1 |  0 |  1 |   0   |
|  1 |  1 |  0 |   0   |
|  1 |  1 |  1 |   1   |



Whereas, in an **odd parity** generator, if the input message has even number of `1`s, the parity bit will be 1. On the other hand, if there are odd number of `1`s, parity bit generated will be 0.

#### Truth Table for an Odd Parity Generator for a 3-bit word

| A  | B  | C  |  PARITY BIT(P)    |
|:-:|:-:|:-:|:-:|:-:|
|  0 |  0 |  0 |   1   |
|  0 |  0 |  1 |   0   |
|  0 |  1 |  0 |   0   |
|  0 |  1 |  1 |   1   |
|  1 |  0 |  0 |   0   |
|  1 |  0 |  1 |   1   |
|  1 |  1 |  0 |   1   |
|  1 |  1 |  1 |   0   |



The parity bit generated is then added to the message to be sent.


### Parity Detector

Parity detector receives the message and checks it for errors. If an error is detected, parity error check bit gives `1` as output and `0` when no error is detected.

#### Truth Table for an Even Parity Detector for a 3-bit word

| A  | B  | C  |  P |   PARITY ERROR CHECK |
|:-:|:-:|:-:|:-:|:-:|---|
| 0  | 0  | 0  | 0  | 0  |
| 0  | 0  | 0  | 1  | 1  |
| 0  | 0  | 1  | 0  | 1  |
| 0  | 0  | 1  | 1  | 0  |
| 0  | 1  | 0  | 0  | 1  |
| 0  | 1  | 0  | 1  | 0  |
| 0  | 1  | 1  | 0  | 0  |
| 0  | 1  | 1  | 1  | 1  |
| 1  | 0  | 0  | 0  | 1  |
| 1  | 0  | 0  | 1  | 0  |
| 1  | 0  | 1  | 0  | 0  |
| 1  | 0  | 1  | 1  | 1  |
| 1  | 1  | 0  | 0  | 0  |
| 1  | 1  | 0  | 1  | 1  |
| 1  | 1  | 1  | 0  | 1  |
| 1  | 1  | 1  | 1  | 0  |

#### Truth Table for an Odd Parity Detector for a 3-bit word

| A  | B  | C  |  P |   PARITY ERROR CHECK |
|:-:|:-:|:-:|:-:|:-:|---|
| 0  | 0  | 0  | 0  | 1  |
| 0  | 0  | 0  | 1  | 0  |
| 0  | 0  | 1  | 0  | 0  |
| 0  | 0  | 1  | 1  | 1  |
| 0  | 1  | 0  | 0  | 0  |
| 0  | 1  | 0  | 1  | 1  |
| 0  | 1  | 1  | 0  | 1  |
| 0  | 1  | 1  | 1  | 0  |
| 1  | 0  | 0  | 0  | 0  |
| 1  | 0  | 0  | 1  | 1  |
| 1  | 0  | 1  | 0  | 1  |
| 1  | 0  | 1  | 1  | 0  |
| 1  | 1  | 0  | 0  | 1  |
| 1  | 1  | 0  | 1  | 0  |
| 1  | 1  | 1  | 0  | 0  |
| 1  | 1  | 1  | 1  | 1  |

Although, parity detector can detect most errors, it has some limitations. Some of them are listed below:
* Error is detected only if there are odd number of error bits.
* Error in parity bit might lead to error detection despite correct transmission.
* Parity detector will not be able to detect errors where both parity and data bit has such error that the parity bit matches.

You can verify the same in circuit given below.

<iframe width="600px" height="400px" src="https://circuitverse.org/simulator/embed/109517" id="projectPreview" scrolling="no" webkitAllowFullScreen mozAllowFullScreen allowFullScreen></iframe>

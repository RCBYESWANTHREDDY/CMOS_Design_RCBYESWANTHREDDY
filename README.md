# CMOS_Circuit_Design
# LECTURE 1

# CMOS Inverter Operation, SPICE Simulation, and Delay Characterization

---

## 1. Structural Overview of the CMOS Inverter

A CMOS inverter consists of a complementary pair of MOS transistors:

- PMOS connected between **VDD** and output  
- NMOS connected between **output** and **VSS (ground)**  
- Gates tied together to form **Vin**  
- Drains tied together to form **Vout**

When:

- **Vin = 0** → PMOS ON, NMOS OFF → Output = VDD  
- **Vin = VDD** → PMOS OFF, NMOS ON → Output = 0  

This complementary switching ensures full voltage swing and minimal static power dissipation.

---

### CMOS Inverter Driving a Load Capacitor

<img width="373" height="537" alt="Screenshot 2026-02-22 at 7 32 22 PM" src="https://github.com/user-attachments/assets/25120d12-4a3f-4881-9f02-d26e8a43e769" />


The output node drives a load capacitance \( C_L \), which directly influences switching delay.

---

## 2. SPICE-Based Transistor Analysis

SPICE simulations enable detailed examination of MOS transistor behavior across operating regions:

- Cutoff  
- Linear (Triode)  
- Saturation  

The inverter transition region occurs when both pull-up and pull-down networks conduct simultaneously.

---

### Drain Current Characteristics
<img width="1050" height="394" alt="Screenshot 2026-02-23 at 10 07 53 AM" src="https://github.com/user-attachments/assets/41a9c43a-6835-4eab-a9dc-6c80fd461527" />

The figure illustrates:

- PMOS and NMOS current variation with input voltage  
- Region of current balance near switching threshold  
- Transition behavior during logic inversion  

---

## 3. Voltage Transfer Characteristic (VTC)

The Voltage Transfer Characteristic defines the static relationship between input voltage and output voltage.

---

### VTC Curve from SPICE

<img width="936" height="486" alt="Screenshot 2026-02-23 at 10 08 36 AM" src="https://github.com/user-attachments/assets/3fd719c5-113c-48c9-afac-be2ebe0acedf" />


Key observations:

- Low Vin → Vout ≈ VDD  
- High Vin → Vout ≈ 0  
- Intermediate Vin → Both devices partially ON  

The slope in the transition region determines switching threshold and noise margins.

---

## 4. Geometry Dependence of MOS Current

Under long-channel approximation:

Id ∝ (W / L)

Where:

- W = channel width  
- L = channel length  

Increasing W improves drive strength and reduces propagation delay.

---

## 5. Propagation Delay and Load Capacitance

During switching, the output capacitance must charge or discharge.

A first-order delay approximation is:

td ≈ (CL × V) / I

Where:
W is transistor width
L is transistor length

Implications:

- Larger load capacitance increases delay  
- Higher drive current decreases delay  

---

## 6. Delay Characterization and Lookup Tables

Repeated SPICE simulation during full-chip timing analysis is computationally expensive.  
Therefore, delay values are pre-characterized and stored in lookup tables indexed by:

- Input slew  
- Output load capacitance  

---


## 7. Clock Tree Synthesis (CTS) Example

In Clock Tree Synthesis:

- Buffers are inserted hierarchically 
- Each level drives comparable capacitive loads  
- Identical buffers are typically used within the same stage 

---

### Two-Level Buffer Tree

<img width="967" height="664" alt="Screenshot 2026-02-22 at 7 33 09 PM" src="https://github.com/user-attachments/assets/984f3f44-d754-4926-8628-fa42a6a22067" />

Assume:

- \( C1 = C2 = C3 = C4 = 25fF \)  
- \( C{buf1} = C{buf2} = 30fF \)

Then:

- Node A total capacitance = 60fF  
- Node B total capacitance = 50fF  
- Node C total capacitance = 50fF  

Balanced loading enables predictable delay behavior.

---

## 8. Delay Table Comparison Between Buffers

Different buffers may implement identical logical functions but differ electrically due to transistor sizing variations.

---

### Delay Table Comparison

<img width="1395" height="437" alt="Screenshot 2026-02-23 at 10 18 22 AM" src="https://github.com/user-attachments/assets/548aa5af-1833-4701-b35c-a5320e9f37ae" />

For a given:

- Input slew (e.g., 60ps)  
- Output load (e.g., 50fF)  

Delay is selected from the corresponding table cell of the chosen buffer type.

---

## 9. How Propagation Delay is Measured in SPICE

Propagation delay is defined as:

td = t(Vout at 50%) − t(Vin at 50%)

Measurement steps:

1. Apply controlled input transition  
2. Attach specified load capacitance  
3. Run transient SPICE simulation  
4. Measure time difference at 50% voltage crossings  

This ensures consistent and repeatable library characterization.

---
# Lecture 2
# DESIGNING THE BASIC ELEMENT IN CIRCUIT DESIGN - NMOS

NMOS is considered as one of the basic elements of circuit design for designing the NMOS 

it should have the following structural charecteristics

<img width="437" height="389" alt="Screenshot 2026-02-25 at 10 27 30 AM" src="https://github.com/user-attachments/assets/5e721363-6744-4985-9011-c064306ea4f1" />

It is a 4‑terminal device:
1. Gate (G)
2. Source (S)
3. Drain (D)
4. Body / Bulk / Substrate (B)

## Physical structure (for an NMOS):

• P-type substrate (forms the body; the channel will be N-type when inverted).

• N+ diffusion regions:

 One is the source
 
 One is the drain
 
• **Isolation regions**: it has two isolation regions to separate one transistor from another.

• Gate oxide(thin SiO₂ layer)grown on the substrate by means of process like etching etc.

• **Polysilicon or metal gate** placed on top of the gate oxide (this is the gate electrode that is used to drive the NMOS).

• **Body terminal** is usually connected to ground ,But thhe main use of body terminal is observed when the potential is applied because it helps to tune the thresold voltage

---

## For PMOS, the structure is essentially the inverted version of NMOS:

• N-type substrate or N-well

• P+ diffusion regions for source and drain

Rest remains the same and channel forms p-type under appropriate gate bias

---

 ## what happens when thresold voltage is zero

 lets first give zero thresold voltage implies VGS = 0, all terminals at 0 V
 
<img width="384" height="323" alt="Screenshot 2026-02-25 at 10 30 25 AM" src="https://github.com/user-attachments/assets/c50c2e36-1efc-49c0-bd84-14c391aaf0d8" />

Next ground the other terminals (Drain,Source,Bulk) 

<img width="405" height="499" alt="Screenshot 2026-02-25 at 10 31 31 AM" src="https://github.com/user-attachments/assets/ef777bca-fab8-4d7d-9ed3-d018af7cfce7" />

This remainds us about PN Junction diode.The device behaves like two back-to-back PN junction diodes (source–body and drain–body). 

<img width="348" height="362" alt="Screenshot 2026-02-25 at 10 32 31 AM" src="https://github.com/user-attachments/assets/65d9cf13-baa4-450c-a34b-9ffe3782a4fa" />

As both Junctions are Off this implies Source drain resistance is high. 

---

## what happens when thresold voltage is applied

Gate becomes positively charged relative to the P-type substrate

<img width="371" height="383" alt="Screenshot 2026-02-25 at 10 34 27 AM" src="https://github.com/user-attachments/assets/965fb932-2708-48c7-8e61-7a7c75ea3c89" />

Gate repeals the positive Charges in the Psubstrate as they are majority carriers because of the positive charge devolped 

 <img width="454" height="414" alt="Screenshot 2026-02-25 at 10 36 40 AM" src="https://github.com/user-attachments/assets/792775f0-727a-4dcb-903c-5600e81167be" />

This push positive charges behind leaving -ve charges  ,It leads to accumulation of negative charges  

<img width="552" height="328" alt="Screenshot 2026-02-25 at 10 37 21 AM" src="https://github.com/user-attachments/assets/69dcf4eb-894e-4956-bf87-7e8b0ea2bad6" />

---

# LECTURE 3

# STRONG INVERSION AND THRESOLD VOLTAGE

**Depletion region ** is formed when you apply reverse bias in a pn junction diode. This means that when a positive voltage is applied to the gate , the majority carriers in this region are depleted. 

In the same fashion, the p‑substrate in a MOS structure also gets depleted of its majority carriers.

<img width="596" height="388" alt="Screenshot 2026-02-25 at 2 40 08 PM" src="https://github.com/user-attachments/assets/6acfde52-5fb1-4a8d-a6ca-3d40af3527e1" />


## STRONG INVERSION

When we increase the gate voltage to a certain level, we observe the following phenomena:

1. As gate voltage increases and becomes more positive, more positive charges are repelled (i.e., more majority carriers are pushed away), leading to an increase in the depletion region width.

2. Continuing to increase the gate voltage, we reach a point where the surface region effectively inverts to behave as an n‑type material. This is called **surface inversion or strong inversion**.

<img width="460" height="387" alt="Screenshot 2026-02-25 at 2 44 24 PM" src="https://github.com/user-attachments/assets/372df757-2633-4771-aff8-9e5b68efc67e" />

## THRESHOLD VOLTAGE

The gate‑to‑source voltage (VGS) required to achieve this inversion is called the **threshold voltage**.

If we increase the gate voltage even further, the electric field tends to attract negative charges (electrons) or repel positive ions, but the region is already depleted of those majority carriers. 

As a result, it attracts electrons from the n+ heavily doped regions (source and drain).

<img width="398" height="265" alt="Screenshot 2026-02-25 at 3 00 05 PM" src="https://github.com/user-attachments/assets/8aad148a-06a5-4884-a91a-9b74b4500392" />

This leads to an increase in the effective channel (inversion layer) conductivity, but there is little to no further change in the depletion layer width. This process leads to the formation of an n‑channel from source to drain.


<img width="389" height="284" alt="Screenshot 2026-02-25 at 3 00 24 PM" src="https://github.com/user-attachments/assets/299f0d35-9ee8-4af3-9ed5-0b6268de6dc4" />


<img width="450" height="98" alt="Screenshot 2026-02-25 at 3 00 48 PM" src="https://github.com/user-attachments/assets/52d01d2f-5a1b-4a73-9a39-ee188258578e" />


## Cut‑off Region Operation

When the gate‑to‑source voltage is below the threshold voltage, no strong inversion  layer (n‑channel) is formed between source and drain. In this case, the MOSFET operates in the cut‑off region, and ideally, no drain current flows.

## Importance of the Body Terminal

The body (or substrate) terminal plays an important role in the device operation, especially through the body effect, which influences the threshold voltage.

**Scenario 1: VSB = 0**

<img width="315" height="335" alt="Screenshot 2026-02-25 at 2 55 43 PM" src="https://github.com/user-attachments/assets/1ed76e14-7dd6-4c79-9163-303b9b0f660c" />

Here, the source and body (substrate) are at the same potential, so the source‑to‑body voltage VSB is zero. The depletion region is determined only by the gate voltage and the built‑in potential of the junction.



**Scenario 2: VSB > 0**

<img width="389" height="284" alt="Screenshot 2026-02-25 at 3 00 24 PM" src="https://github.com/user-attachments/assets/db82f2ab-9224-464e-9715-14adda1dba82" />

In this scenario, a positive potential is applied to the source and a more negative potential is applied to the body, so the source‑to‑body voltage VSB is a positive value (source is at a higher potential than the body).

**1st Observation**
The depletion region on the side where the body is connected becomes wider compared to Scenario 1, due to the additional reverse bias across the source‑body junction. There is no significant change in the depletion region on the other side.


**2nd Observation**

Because of this additional reverse bias, the onset of inversion at the surface is slightly delayed. In other words, a higher gate‑to‑source voltage is now required to reach strong inversion. This means the threshold voltage increases when VSB is positive.
  
----
 
 







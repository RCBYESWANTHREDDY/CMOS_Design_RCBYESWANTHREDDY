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

  

 
 







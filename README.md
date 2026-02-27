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

**Depletion region** is formed when you apply reverse bias in a pn junction diode. This means that when a positive voltage is applied to the gate , the majority carriers in this region are depleted. 

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

When the gate‑to‑source voltage is below the threshold voltage, no strong inversion layer (n‑channel) is formed between source and drain. In this case, the MOSFET operates in the cut‑off region, and ideally, no drain current flows.

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

# LECTURE 4

# Threshold voltage with positive substrate potential

## WHAT happens after application of gate to source voltage 

<img width="672" height="387" alt="Screenshot 2026-02-25 at 4 19 11 PM" src="https://github.com/user-attachments/assets/f884ceb0-ea30-48b2-95cb-0df77b7b196c" />

When gate-to-source voltage is applied, the depletion width increases in both cases.

In the positive VSB case, the body connection attracts negatively charged particles. This attraction reduces the tendency for surface inversion at first. So, surface inversion is delayed when VSB is positive.

<img width="665" height="399" alt="Screenshot 2026-02-25 at 4 22 52 PM" src="https://github.com/user-attachments/assets/4f2fb367-d0e8-497c-9040-d0683d7ac71e" />

**In the zero body-bias case (VSB = 0)**, surface inversion happens earlier. The voltage at which surface inversion starts in this case is called VTO.

 <img width="306" height="352" alt="Screenshot 2026-02-25 at 4 26 26 PM" src="https://github.com/user-attachments/assets/6c5bd968-3b84-40d0-ae2d-7d38c22d9f6e" />

**In the positive VSB case**, this early surface inversion does not occur. We need an additional voltage, call it V1, on the gate to achieve surface inversion. So the new threshold voltage becomes VTO + V1.

 <img width="400" height="418" alt="Screenshot 2026-02-25 at 4 26 49 PM" src="https://github.com/user-attachments/assets/86979484-5558-4e94-851f-a86d660e4156" />


**Conclusion:** With positive source-to-body voltage (VSB > 0), the threshold voltage increases. This effect is called the body effect (or substrate bias effect). 

<img width="526" height="57" alt="Screenshot 2026-02-25 at 4 30 36 PM" src="https://github.com/user-attachments/assets/aa9ef5bf-0d3d-420f-a6aa-6764105bb75d" />

---

## Threshold voltage equation with body effect

**VT = VTO + γ ( √(2ϕF + VSB) − √(2ϕF) )**
 
Where: 
VT  is the threshold voltage with body bias.
VTO is the threshold voltage when VSB = 0.
γ   is the body effect coefficient. ϕF  is the Fermi potential.
VSB is the source-to-body voltage.

<img width="373" height="162" alt="Screenshot 2026-02-25 at 4 34 43 PM" src="https://github.com/user-attachments/assets/d72e67cc-985d-42c3-a0cc-babeaf9e2b07" />

These parameters depend on the technology and process. If VSB = 0, then VT = VTO. 
If VSB is not zero, 
we need extra gate voltage to reach surface inversion. 

<img width="219" height="26" alt="Screenshot 2026-02-25 at 4 33 47 PM" src="https://github.com/user-attachments/assets/8aa4a7eb-21b8-4482-b343-9e114aedd3b8" />

### Body effect coefficient (γ):

**γ** depends on device and process parameters like oxide thickness and substrate doping. γ controls how strongly VT changes with VSB.


<img width="302" height="219" alt="Screenshot 2026-02-25 at 4 38 11 PM" src="https://github.com/user-attachments/assets/ce617af7-70d9-45d8-9c9e-f70e2842cad0" />

Once VTO, γ, and ϕF are given, a SPICE tool calculates VT for any VSB. 

That VT value represents the effective threshold voltage of the device under body bias

---
# Day 1 PART 2 Lecture 1

# Resistive region of operation with small drain-source voltage

There are 3 modes of operations 
1. cuttoff mode

2 .Resistive mode 

3 .saturation mode

## Resistive mode of operation


If Vgs is increased there will be more charge carriers in the channel and more conducting area between source and drain 

<img width="366" height="254" alt="Screenshot 2026-02-26 at 2 55 02 PM" src="https://github.com/user-attachments/assets/0d97143b-6f81-42fc-8d35-11a47fe7714e" />

  <img width="363" height="267" alt="Screenshot 2026-02-26 at 2 55 41 PM" src="https://github.com/user-attachments/assets/5232b524-ea75-4afc-9cfb-6304f3f4a405" />

  <img width="367" height="304" alt="Screenshot 2026-02-26 at 2 56 33 PM" src="https://github.com/user-attachments/assets/deed57e9-56b2-4c31-819f-c04665ba2380" />

From the above three images if we increase vgs channel width increases more is due to induced charges due to gate voltage is proportional to gate voltage 

<img width="212" height="28" alt="Screenshot 2026-02-26 at 2 59 04 PM" src="https://github.com/user-attachments/assets/c1a71960-fdfe-4319-ba81-128ee696e716" />


# Analyze at vgs = 1 v

<img width="386" height="311" alt="Screenshot 2026-02-26 at 3 01 47 PM" src="https://github.com/user-attachments/assets/b7b7a141-c4c7-490a-ae87-fb9ccdec899e" />

Vgs > Vt, the transsistor is turned on

<img width="261" height="311" alt="Screenshot 2026-02-26 at 3 03 34 PM" src="https://github.com/user-attachments/assets/1a25f3a5-55bb-4210-a2d7-4758fe4561d9" />

we have voltage gradient because of application of vds before it was constant

<img width="411" height="294" alt="Screenshot 2026-02-26 at 3 06 37 PM" src="https://github.com/user-attachments/assets/a8299db4-e3b0-421b-8aeb-ccbc5413dbd3" />

**Effective channel length** is much less than expected because of fabrication techniques

## voltage across channel length

<img width="276" height="303" alt="Screenshot 2026-02-26 at 3 11 45 PM" src="https://github.com/user-attachments/assets/23503f76-69f1-4505-bc24-f3318a73c0f7" />

<img width="264" height="64" alt="Screenshot 2026-02-26 at 3 12 12 PM" src="https://github.com/user-attachments/assets/bbf09c55-cdc4-4db4-b347-c7bfa06c7752" />

we observe difference in voltage is due to application of vds 

V(x) is the voltage at any point x on channel 

V(0) = 0 ; 

V(L) = Vds

Before application of Vds at every point the voltage is Vgs 

After application of Vds voltage the voltage is Vgs-V(x) is considered as **Effective voltage**

---

# Day 1 part2 Lecture 2

# Drift current theory

<img width="412" height="334" alt="Screenshot 2026-02-26 at 3 32 43 PM" src="https://github.com/user-attachments/assets/7c61b9bf-a404-4d75-9a92-253d0802da13" />

![WhatsApp Image 2026-02-26 at 15 33 39](https://github.com/user-attachments/assets/728e06e1-3e48-47d4-bb39-df75850ffd91)

# Induced charge 

<img width="258" height="87" alt="Screenshot 2026-02-26 at 4 21 22 PM" src="https://github.com/user-attachments/assets/298141a6-021e-4950-aab7-266b496db290" />

this is based on charge conservation principle

## First order analysis

<img width="257" height="242" alt="Screenshot 2026-02-26 at 4 23 38 PM" src="https://github.com/user-attachments/assets/2faea311-655c-4fe4-b3bc-57c8fe7485ca" />

There are two different currents 

1. **DRIFT CURRENT** due to potential difference

2. **DIFFUSION CURRENT** due to diiference in carrier concentration

<img width="682" height="338" alt="Screenshot 2026-02-26 at 4 26 43 PM" src="https://github.com/user-attachments/assets/25dc269b-5d19-4cdf-a627-3a49e658ce17" />

we have drift current in our case 

## Drift current 


<img width="243" height="67" alt="Screenshot 2026-02-26 at 4 30 17 PM" src="https://github.com/user-attachments/assets/8819213c-5a41-4e14-9828-732217bbe6ba" />

**channel width** from top level

<img width="680" height="391" alt="Screenshot 2026-02-26 at 4 29 16 PM" src="https://github.com/user-attachments/assets/d83b473b-0945-4839-a1ac-f3a836d88be4" />

drift current is a function of channel width.
To get the drift current we need to integrate velocity and available charge over channel width

---

# Day 1 part2 Lecture 3

# Drain current model for linear region of operation

<img width="253" height="91" alt="Screenshot 2026-02-26 at 4 38 00 PM" src="https://github.com/user-attachments/assets/95908493-ea18-4b57-a841-dd6f7d8d23fb" />

<img width="183" height="16" alt="Screenshot 2026-02-26 at 4 38 20 PM" src="https://github.com/user-attachments/assets/b7bd298b-6d98-4d38-bb90-613b4cc12292" />

substituting v(n) and qi(x) values and integrate over channel length

<img width="269" height="77" alt="Screenshot 2026-02-26 at 4 39 46 PM" src="https://github.com/user-attachments/assets/f7c80706-c7af-456e-af25-e746b86935fc" />

we need to integrate length from 0 to L and and voltage from 0 to vds
we get

<img width="273" height="170" alt="Screenshot 2026-02-26 at 4 41 49 PM" src="https://github.com/user-attachments/assets/4da2bf8a-bf04-4add-b6b1-26f3e3d3581c" />

we observe quadratic relation with width but we need linear relation so simplify it further 

substituting **process transconductance**

<img width="270" height="33" alt="Screenshot 2026-02-26 at 4 44 20 PM" src="https://github.com/user-attachments/assets/4f935b97-1146-4ab7-a489-b0a625c89e2c" />

we get 

<img width="258" height="39" alt="Screenshot 2026-02-26 at 4 45 04 PM" src="https://github.com/user-attachments/assets/72a4a617-6186-4d07-89f9-a0e983dc4abb" />

we still need to get first order relation , before that substituting givenvalues in equation we get

<img width="417" height="238" alt="Screenshot 2026-02-26 at 4 48 17 PM" src="https://github.com/user-attachments/assets/b4e5f70d-8c0d-4c91-83fb-f1ed9512b140" />

for all values vds <= (vgs-vt) the mosfet operates in linear region 

---

# Day 1 part2 Lecture 4

# SPICE conclusion to resistive operation

## impact of vgs and vt on drain current

Vgs is varied from 0.5 to 2.5 v in increamental intervels of 0.5
so we get (Vgs-Vt) accordingly 

<img width="297" height="97" alt="Screenshot 2026-02-26 at 4 55 37 PM" src="https://github.com/user-attachments/assets/fbdb3d22-dcf4-4622-a015-23ee96a12589" />

Vgs = 0.5 v

<img width="290" height="112" alt="Screenshot 2026-02-26 at 4 56 27 PM" src="https://github.com/user-attachments/assets/c01ccfdc-0657-48ab-aeaf-48d8f1fabcc8" />

Vgs = 1  v

<img width="324" height="120" alt="Screenshot 2026-02-26 at 4 57 41 PM" src="https://github.com/user-attachments/assets/3a83cc76-19ae-4e02-9a60-16965159dc53" />

Vgs = 1.5 v

<img width="291" height="113" alt="Screenshot 2026-02-26 at 4 58 51 PM" src="https://github.com/user-attachments/assets/79ae9449-2104-4d7b-80d3-5b6b4193af63" />

Vgs = 2 v

<img width="343" height="115" alt="Screenshot 2026-02-26 at 4 59 09 PM" src="https://github.com/user-attachments/assets/7f1d03d3-9f6b-4c75-876a-416c06921a45" />

Vgs = 2.5 v

<img width="301" height="137" alt="Screenshot 2026-02-26 at 4 59 21 PM" src="https://github.com/user-attachments/assets/e2e6bbb0-249b-4f02-b3b3-cfee429e934e" />

from the above observations if voltage is applied 0.5 we can sweed vds till 0.45 v in order to operate the mosfet in linear region

## how to calculate Id for different values of Vgs

we use spice simulations to do that .

---

#  Day 1 part2 Lecture 5

# Pinch-off region condition

## saturation region

we observe what happens if we increase the value of Vds

we keep Vgs and Vt constant and increase Vds 


<img width="664" height="336" alt="Screenshot 2026-02-26 at 5 06 20 PM" src="https://github.com/user-attachments/assets/7d84e0d0-5d0e-4e21-8e17-f4bf5e3f3ee5" />


Till Vds <= 0.45 v ,channel voltage is greater than Vt so we can see conducting channel from source to drain


<img width="304" height="181" alt="Screenshot 2026-02-26 at 5 10 16 PM" src="https://github.com/user-attachments/assets/47a2fef3-22a9-49bf-8ee4-79b1093116b9" />


<img width="394" height="297" alt="Screenshot 2026-02-26 at 5 10 44 PM" src="https://github.com/user-attachments/assets/c7422ce7-c3a6-4b3e-ae54-155ef85b22f3" />


at vds = 0.55 v , surface inversion happens and  channel voltage is equal thresold voltage


<img width="288" height="47" alt="Screenshot 2026-02-26 at 5 11 18 PM" src="https://github.com/user-attachments/assets/922509e2-2f3a-454c-a7a1-719ae9d91084" />


<img width="316" height="322" alt="Screenshot 2026-02-26 at 5 11 43 PM" src="https://github.com/user-attachments/assets/18f5e58f-b6e8-457b-b220-5852e0d5c27e" /> 


<img width="305" height="304" alt="Screenshot 2026-02-26 at 5 13 49 PM" src="https://github.com/user-attachments/assets/71f7c650-1385-4f16-aa0f-42bc63389001" />


at vds >= 0.55 , channel voltage is less than thresold voltage channel disappears
this conditon is known as **Saturation region**


<img width="278" height="106" alt="Screenshot 2026-02-26 at 5 15 36 PM" src="https://github.com/user-attachments/assets/167da0bf-0eb4-4cc3-92f8-86f888a94c71" /> 


<img width="348" height="333" alt="Screenshot 2026-02-26 at 5 15 49 PM" src="https://github.com/user-attachments/assets/545a94b1-a2c9-4b8f-9af5-210262e85863" />

---

#  Day 1 part2 Lecture 6

#  Drain current model for saturation region of operation

In saturation region voltage is constant 

<img width="378" height="315" alt="Screenshot 2026-02-26 at 5 58 08 PM" src="https://github.com/user-attachments/assets/a66b8e21-9711-4377-b7c4-13cce6882b3f" />

No dependency in vds in saturation region

<img width="249" height="161" alt="Screenshot 2026-02-26 at 7 28 24 PM" src="https://github.com/user-attachments/assets/f6110f1b-4848-4be8-960b-f0752d4a3c29" />

Replace Vds by Vgs - Vt

We get drain current in saturation region

<img width="251" height="154" alt="Screenshot 2026-02-26 at 7 32 48 PM" src="https://github.com/user-attachments/assets/d6a1716a-f0e8-4da3-9969-d7c7dc7ab3c0" />

it is no longer linear and we have less terms to deal with
Looks like perfect current source implies current is constant but it is not true 

<img width="577" height="238" alt="Screenshot 2026-02-26 at 7 34 50 PM" src="https://github.com/user-attachments/assets/4e2ac7c9-5db3-44bd-98e9-9110014f6a6a" />

Vds is increasedchannel length is still modulated not constant.
That depencency is **channel length modulation**

<img width="461" height="120" alt="Screenshot 2026-02-26 at 7 36 57 PM" src="https://github.com/user-attachments/assets/fd3a5145-169d-4e0c-a939-0f654dccdb26" />

So this is drain current equation in saturation region

---
# Day 1 Part 3 Lecture 1
# Basic SPICE setup

Spice is a software which generates delay waveforms from the input which defines the MOSFETS
Our MOSFET 

<img width="293" height="268" alt="Screenshot 2026-02-26 at 7 45 38 PM" src="https://github.com/user-attachments/assets/56b29fc4-59d3-42a0-bac0-8a3d59b6de3f" />

Elements defining MOSFET 

**THRESHOLD VOLTAGE**

<img width="289" height="175" alt="Screenshot 2026-02-26 at 7 47 03 PM" src="https://github.com/user-attachments/assets/ed852dd2-4c13-445d-9c20-31115e208cf9" />

**DRAIN CURRENT IN LINEAR REGION**

<img width="254" height="72" alt="Screenshot 2026-02-26 at 7 49 01 PM" src="https://github.com/user-attachments/assets/d28caefc-0f73-4674-a47f-41ddc6ee8cd8" />

**DRAIN CURRENT IN SATURATION REGION**

<img width="285" height="74" alt="Screenshot 2026-02-26 at 7 49 20 PM" src="https://github.com/user-attachments/assets/4205f049-c7f5-480b-b1c3-a150e4328d4e" />

Technological constants are highlighted in yellow . no need to derive they come from foundaries. These are called SPICE model parameters

<img width="478" height="328" alt="Screenshot 2026-02-26 at 7 50 02 PM" src="https://github.com/user-attachments/assets/8b339c56-d58b-4df5-bea5-95b92373e3f4" />

Next we give SPICE net list also to spice software

<img width="208" height="192" alt="Screenshot 2026-02-26 at 7 51 33 PM" src="https://github.com/user-attachments/assets/ba90f2ab-be8f-4493-8ddf-2f270784bea0" />

we get

<img width="161" height="110" alt="Screenshot 2026-02-26 at 7 51 50 PM" src="https://github.com/user-attachments/assets/bf8b7c3d-e519-4f27-ba5a-0be33940e8cd" />

## Details of SPICE netlist

<img width="601" height="250" alt="Screenshot 2026-02-26 at 7 54 38 PM" src="https://github.com/user-attachments/assets/65e551f9-3040-4e8c-8b70-5d8464f70b37" />

MOSFET can be represented in the form of circuit and role of resistor is stop feeding current directly to gate as it may damage the MOSFET

all Vss is variable so we control them to get waveforms in one go

<img width="299" height="211" alt="Screenshot 2026-02-26 at 7 58 16 PM" src="https://github.com/user-attachments/assets/ec0b166b-4fe8-48d9-9dd8-0635abb77eaa" />

so we feed this data to SPICE software

---
# Day 1 Part 3 Lecture 2
# Circuit description in SPICE syntax

we need to write SPICE data in correct syntax just like c programming has its own syntax SPICE has its own syntax

**STEP 1 :**  Defining Nodes

lets assign values to the circuit

<img width="279" height="198" alt="Screenshot 2026-02-26 at 8 04 20 PM" src="https://github.com/user-attachments/assets/3d5919c8-abff-4357-9a94-dab9049bc4af" />

we need to create nodes in order to feed anything like R1 it needs to be in between two nodes in order SPICE to understand the given command

<img width="341" height="294" alt="Screenshot 2026-02-26 at 8 08 16 PM" src="https://github.com/user-attachments/assets/b6a9a43d-0b58-4b14-95d6-6ab7329e44fb" />

These are the nodes and they are given names 

**STEP 2 :** Feeding the values

First MOSFET name

<img width="643" height="235" alt="Screenshot 2026-02-26 at 8 14 56 PM" src="https://github.com/user-attachments/assets/4d8c3d42-d015-4738-be9a-074c4d795213" />

Second Drain

<img width="651" height="279" alt="Screenshot 2026-02-26 at 8 15 37 PM" src="https://github.com/user-attachments/assets/877812e6-143f-4c34-bb00-fa3715055a5d" />

Third Source

<img width="670" height="242" alt="Screenshot 2026-02-26 at 8 16 20 PM" src="https://github.com/user-attachments/assets/aa0b4c33-8110-471f-8ace-71a486e58654" />

Fourth Substrate

<img width="660" height="239" alt="Screenshot 2026-02-26 at 8 17 16 PM" src="https://github.com/user-attachments/assets/00022a2f-422d-47de-ac18-7b897f732c6a" />

Fifth MOSFET NAME

<img width="650" height="241" alt="Screenshot 2026-02-26 at 8 19 27 PM" src="https://github.com/user-attachments/assets/8e304822-25c2-4b65-b8fd-8ca182808d90" />

SIXTH width of Gate 

<img width="627" height="269" alt="Screenshot 2026-02-26 at 8 20 09 PM" src="https://github.com/user-attachments/assets/44b05d41-e68a-44b3-baa0-65c8a9277ee6" />

 Seventh Length of Gate
 
 <img width="635" height="257" alt="Screenshot 2026-02-26 at 8 21 14 PM" src="https://github.com/user-attachments/assets/313a10c9-e2cf-4737-ba1e-c1c19ed85a96" />

same fashion we define resistor

<img width="119" height="22" alt="Screenshot 2026-02-26 at 8 22 38 PM" src="https://github.com/user-attachments/assets/95979f40-0f94-4745-99fa-9e950f784e84" />
The order is First Terminal , Second Terminal , Resistance value

Next Vdd ( DRAIN VOLTAGE)

<img width="137" height="24" alt="Screenshot 2026-02-26 at 8 24 44 PM" src="https://github.com/user-attachments/assets/98f49278-e85c-4f7d-a3c0-6596caee296a" />

The order is First Terminal , Second Terminal , Drain voltage value

Next Vin ( GATE VOLTAGE )

<img width="134" height="32" alt="Screenshot 2026-02-26 at 8 26 11 PM" src="https://github.com/user-attachments/assets/8d724928-1b2a-45e7-a245-740d9765148e" />

The order is First Terminal , Second Terminal ,Gate voltage value

---
# Day 1 Part 3 Lecture 3
# Define technology parameters

Next , we need to get model of nmos 

once we have all constants it becomes easy to find out the NMOS model 

These are model parameters they come in package 

<img width="198" height="138" alt="Screenshot 2026-02-26 at 8 36 29 PM" src="https://github.com/user-attachments/assets/940658d5-721c-4141-8f6c-42a0bd825f0f" />

For this nmos model 

 <img width="281" height="86" alt="Screenshot 2026-02-26 at 8 37 28 PM" src="https://github.com/user-attachments/assets/ddb6de7d-00d8-4950-99ee-225aa4b161d5" />

 
For this pmos model 

<img width="298" height="77" alt="Screenshot 2026-02-26 at 8 39 25 PM" src="https://github.com/user-attachments/assets/3991b58e-467c-4b9e-be22-8c7eaaf48341" />

Package the models

<img width="309" height="157" alt="Screenshot 2026-02-26 at 8 41 32 PM" src="https://github.com/user-attachments/assets/7704928b-464c-4311-abc3-de09237c385c" />

just name the sections and give simulation commands


<img width="508" height="293" alt="Screenshot 2026-02-26 at 8 45 00 PM" src="https://github.com/user-attachments/assets/61056df8-dab3-4b9d-9281-d5eda8388f5c" />

This is done to calculate drian current at different values of Vgs

---
# Day 1 Part 3 Lecture 4
# First SPICE simulation


---

# Day 2 part 1 lecture 1
# SPICE simulation for lower nodes

Resulted waveform of SPICE simulation where we have **Drain current** in y axis and **Sweep voltage** in the x axis 

<img width="611" height="357" alt="Screenshot 2026-02-26 at 9 18 46 PM" src="https://github.com/user-attachments/assets/ae950e16-0507-47fe-9e62-66ba21cda4a2" />

**OBSERVATIONS** 

1. At Vgs = 0 ;  Id( Drain current) = 0 and  Vgs = 0.5 V curve almost intersects with that curve 

2. All the equations we calculated are encapsulated in this curves

<img width="611" height="379" alt="Screenshot 2026-02-26 at 9 26 09 PM" src="https://github.com/user-attachments/assets/5de754d8-e625-467c-9158-de3670c34f6a" />

3. From this curve we can see that

In **LINEAR REGION**  for the lower values of Vds , (Vds)2/2 term tends to zero
 Drain current is linear function of (Vds)

similarly in **Saturation region** it shows dependency  with lambda not completely saturated and not completely linear but it appears to be constant

**CASE 2** 

Every thing remains same only changes are W = 0.375 u and L = 0.25 u
Rest all the factors remains same

<img width="566" height="368" alt="Screenshot 2026-02-26 at 10 56 50 PM" src="https://github.com/user-attachments/assets/3d7826d2-5b68-4dd5-a88b-e21676a26a29" />

we get this curve as output 

COMPARING BOTH CURVES 

<img width="686" height="323" alt="Screenshot 2026-02-27 at 12 36 57 AM" src="https://github.com/user-attachments/assets/b823f6ab-7a35-4333-955e-29549a00a067" />

---


# Day 2 part 1 lecture 2

# Drain current vs gate voltage for long and short channel device

**Observations** from comparing two curves 

1 st observation is

<img width="394" height="330" alt="Screenshot 2026-02-27 at 12 42 47 AM" src="https://github.com/user-attachments/assets/031843a4-caa9-4ffd-b351-cb64ffc0cd44" />

<img width="369" height="303" alt="Screenshot 2026-02-27 at 12 43 33 AM" src="https://github.com/user-attachments/assets/a47c715c-7738-4bcc-a50a-135f44de1ba1" />

In Long channel device the drain current relation is quadratic where as in short channel device at starting the dependency is quadratic at low voltage but it becomes linear at later stages. Reason is **velocity saturation**

## Drain current vs Gate voltage new simulation

only change we do is in dc voltage line sweep in step 2.5

<img width="233" height="158" alt="Screenshot 2026-02-27 at 12 48 27 AM" src="https://github.com/user-attachments/assets/8cf33acf-1cfb-49ad-bb4b-340bd2ba7888" />

**Curve for 1.2 u**

<img width="505" height="361" alt="Screenshot 2026-02-27 at 12 50 12 AM" src="https://github.com/user-attachments/assets/5cd40a9f-556e-40f2-b504-35fd22bc62d2" />

Comparing it with **Curve for 0.8 u**

<img width="713" height="357" alt="Screenshot 2026-02-27 at 12 51 39 AM" src="https://github.com/user-attachments/assets/ef5ed43a-655f-41c9-af2b-75796d6a76fd" />

we observe drain current of short length channel one has linear dependency while the other one has quadratic relation

---

# Day 2 part 1 lecture 3

# Velocity saturation at lower and higher electric fields

## velocity saturation effect
 
This is observed in short channel devices

<img width="695" height="336" alt="Screenshot 2026-02-27 at 1 07 28 AM" src="https://github.com/user-attachments/assets/5a43b513-ea53-47c1-be6e-6a5993113be1" />

This will eventually become region of operation (Fourth mode)

**Velocity saturation** says for lower values of electric fields the velocity is linear later it saturates

 <img width="568" height="209" alt="Screenshot 2026-02-27 at 1 10 29 AM" src="https://github.com/user-attachments/assets/088fcfff-c02e-4601-a600-2d3e2e93dc58" />

## Derivation

<img width="329" height="78" alt="Screenshot 2026-02-27 at 1 11 30 AM" src="https://github.com/user-attachments/assets/6d338631-8472-4bed-9f90-1f3cedd9e3da" />

at E = Ec
 
<img width="651" height="251" alt="Screenshot 2026-02-27 at 1 12 35 AM" src="https://github.com/user-attachments/assets/0f0ee020-8aa5-4550-895a-d4d484e093bf" />

**Simplified model**

<img width="579" height="280" alt="Screenshot 2026-02-27 at 1 14 44 AM" src="https://github.com/user-attachments/assets/aa4fa2e0-56a4-47df-ae7e-7114d24ad85e" />

---

# Day 2 part 1 lecture 4
# Velocity saturation drain current model

## Drain current Model

<img width="569" height="317" alt="Screenshot 2026-02-27 at 1 18 24 AM" src="https://github.com/user-attachments/assets/043f02cb-29bf-49fe-9055-20968fcd9cfe" />

## Drain current for each region of operations

**Saturation region**

<img width="397" height="144" alt="Screenshot 2026-02-27 at 1 20 34 AM" src="https://github.com/user-attachments/assets/7fe0d34b-ffb1-4aad-bf41-3257d05573ea" />

**Resistive region**

<img width="391" height="206" alt="Screenshot 2026-02-27 at 1 21 35 AM" src="https://github.com/user-attachments/assets/47179629-4cd6-48c0-b4c2-75c69d0b20d2" /> 

lambda vds term becomes zero 

**Velocity saturation region**

Vdsat is only available only for short channel devices

<img width="434" height="213" alt="Screenshot 2026-02-27 at 1 25 19 AM" src="https://github.com/user-attachments/assets/63da3d53-9d84-4a23-9b8d-cdf90f267aba" />

**Observation 2** 

Velocity saturation cause device to saturate early so we observe peak current difference

<img width="690" height="341" alt="Screenshot 2026-02-27 at 1 27 27 AM" src="https://github.com/user-attachments/assets/452fbdfb-afb0-4b77-93a7-32c9d06e6084" />

---

# Day 2 Part 2 Lecture 1
# MOSFET as a switch

## CMOS Voltage-Transfer Characteristics (VTC)

The Voltage-Transfer Characteristic (VTC) describes how the output voltage of CMOS inverter responds to changes in input voltage .

## MOS Transistor

MOS transistor has three terminals: Gate (G) Source (S) , and Drain (D)

<img width="332" height="250" alt="Screenshot 2026-02-27 at 9 36 49 AM" src="https://github.com/user-attachments/assets/ac1d0f5e-1cf1-4c39-be86-a19a831315b4" />

When the gate-to-source voltage |Vgs| is applied, it is shown by arrows indicating the voltage direction between gate and source. The gate voltage controls whether current can flow between Source and Drain

<img width="540" height="222" alt="Screenshot 2026-02-27 at 9 38 13 AM" src="https://github.com/user-attachments/assets/71b090db-78c0-401b-9f0e-10ece67d0552" />

## Transistor as a Switch

Depending on the gate voltage relative to the threshold voltage (Vt) , the transistor either opens or closes the channel between Source and Drain

The switch has the following two operating conditions:

1.With infinite OFF resistance when |Vgs| < |Vt| — no current flows, switch is open.

2. With finite ON resistance when |Vgs| > |Vt| — channel is formed, current flows, switch is closed.

<img width="572" height="296" alt="Screenshot 2026-02-27 at 9 40 59 AM" src="https://github.com/user-attachments/assets/ff36258c-1213-45eb-8022-3e4162de5c71" />

**Observations**

1. When |Vgs| > |Vt|, the transistor is in the ON state and behaves like a resistor  between source and drain.

2. When |Vgs| < |Vt|, the transistor is OFF and acts like an open circuit — no conducting path exists from source to drain.

<img width="542" height="284" alt="Screenshot 2026-02-27 at 9 43 19 AM" src="https://github.com/user-attachments/assets/df046c49-cc23-4f91-b848-9c37d65c7b84" />

## CMOS Inverter with Load Capacitance

The CMOS inverter is formed by connecting one PMOS transistor and one NMOS transistor in a complementary arrangement

**Connection**

1. The gate terminals of both transistors are tied together and receive the input voltage Vin.
 
2. The drain terminals of both transistors are tied together and give the output voltage Vout.

3. A load capacitance CL is connected at the output node.
  
<img width="274" height="243" alt="Screenshot 2026-02-27 at 9 48 28 AM" src="https://github.com/user-attachments/assets/579a53c6-39c2-42fe-8e32-c46fa053debd" />

4. The supply voltage Vdd is connected to the Source of the PMOS transistor.

5. The Source of the NMOS transistor is connected to ground.

## Case : Vin is HIGH and equal to Vdd

### Vin = Vdd: Transistor States and Output

NMOS transistor determines the circuit behaviour at the output node

<img width="678" height="397" alt="Screenshot 2026-02-27 at 9 56 33 AM" src="https://github.com/user-attachments/assets/aaf7925a-576c-4647-ab21-c2541a8bf0e1" />


**observations**

PMOS turns OFF because (VgsP) = 0 < (VtP). The PMOS behaves like an open circuit there is no conducting path from Vdd to Vout through the PMOS side

NMOS turns ON because (VgsN) = (Vdd) > (Vtn). The NMOS behaves like a resistance Rn connected between Vout and Vss.

The load capacitance CL discharges through Rn to ground.

A direct conducting path exists between Vout and Vss because of Rn.

Because the only path at the output connects Vout to Vss is through Rn, the output voltage in steady state will be pulled down to Vss = 0.

---

# Day 2 Part 2 Lecture 2 

# Introduction to standard MOS voltage current parameters

## CMOS Inverter – Switching Analysis

### Equivalent Circuit for Vin = Vdd

The equivalent circuit for Vin = Vdd shows the PMOS is replaced by an open switch and the NMOS is replaced by resistance Rn.
The output node is connected with Vss through Rn and has the load capacitance CL in parallel.

<img width="673" height="346" alt="Screenshot 2026-02-27 at 10 09 03 AM" src="https://github.com/user-attachments/assets/3990af4f-4d6f-4bf4-971f-9aae723a73d3" />


**Observations**

From the equivalent circuit we observe :
1.When Vin = Vdd, direct path exists between Vout and Vss through NMOS resistance Rn.
2. This results in Vout = 0 are observed in steady state 

3. The CL discharges through Rn during falling output transition.

<img width="670" height="376" alt="Screenshot 2026-02-27 at 10 13 13 AM" src="https://github.com/user-attachments/assets/a9eff3d8-baac-4a51-a44d-4ebcd3c70526" />

## Case 2: Vin is LOW and equal to 0 V

<img width="569" height="392" alt="Screenshot 2026-02-27 at 10 16 05 AM" src="https://github.com/user-attachments/assets/52b9b12a-098f-4385-934a-0e1669aa031d" />

PMOS turns ON acts as resistance Rp between Vdd and Vout
NMOS turns OFF acts as an open circuit between Vout and Vss

 ### Equivalent Circuit for Vin = 0

NMOS replaced by open switch and the PMOS replaced by resistance Rp. Output node is connected to Vdd through Rp and has load capacitance CL at the output.

<img width="689" height="391" alt="Screenshot 2026-02-27 at 10 17 28 AM" src="https://github.com/user-attachments/assets/26dce764-794b-4234-9581-b5acef071455" /> 

From observation of the equivalent circuits,currents flowing through PMOS (IdsP) and NMOS (IdsN) must be equal and opposite since they share same drain node. Therefore IdsP = -IdsN.

---
### comparing both equivalent circuits 

Both equivalent circuits placed side by side 

<img width="688" height="310" alt="Screenshot 2026-02-27 at 10 19 53 AM" src="https://github.com/user-attachments/assets/5ebdb8b1-a28e-448f-96e8-0dc47052cdf3" />

## PMOS and NMOS Terminal Labels

<img width="679" height="371" alt="Screenshot 2026-02-27 at 10 25 42 AM" src="https://github.com/user-attachments/assets/e0ff4be1-e6e9-4f72-bce6-312e30dc5105" />

## Voltages and Currents in the Circuit
 From observation of the CMOS inverter circuit, the terminal voltages for NMOS and   PMOS are:

 VgsN = Vin - Vss = Vin
 VdsN = Vout
 VgsP = Vin - Vdd
 VdsP = Vout - Vdd

 ---
# Day 2 Part 2 Lecture 3

# PMOS/NMOS drain current v/s drain voltage

<img width="663" height="289" alt="Screenshot 2026-02-27 at 10 31 55 AM" src="https://github.com/user-attachments/assets/58900d5b-6d2f-45cc-ad08-42eacc737264" />
The two reference equivalent circuits show:

When Vin = Vdd → Vout = 0 (NMOS conducting through Rn, PMOS open);

When Vin = 0 → Vout = Vdd (PMOS conducting through Rp, NMOS open).

## Deriving the NMOS Terminal Voltages

VgsN = Vin - Vss = Vin - 0 = Vin

VdsN = Vout - Vss = Vout - 0 = Vout

<img width="666" height="367" alt="Screenshot 2026-02-27 at 10 33 22 AM" src="https://github.com/user-attachments/assets/c6c04b87-0c3d-4855-b2d5-1bbac4c7715a" />

for the NMOS transistor, the gate-to-source voltage equals to the input voltage directly, and the drain-to-source voltage equals to the output voltage directly

## Deriving the PMOS Terminal Voltages

VgsP = Vin - Vdd
VdsP = Vout - Vdd

Vin ranges from 0 to Vdd, VgsP will be negative quantity (from -Vdd to 0), which is consistent with PMOS operation. 

Similarly VdsP will be a negative when Vout is less than Vdd, which is also consistent with PMOS operation

<img width="661" height="377" alt="Screenshot 2026-02-27 at 10 36 26 AM" src="https://github.com/user-attachments/assets/c141d450-9ebd-4c57-8e2d-bca7bdffa1bf" />

## Relationship Between PMOS and NMOS Currents

IdsP = -IdsN

## NMOS IdsN vs VdsN Curve

Each curve shows two regions:

Linear region — for small VdsN, IdsN increases approximately linearly with VdsN.

Saturation region — for larger VdsN, IdsN levels off and becomes approximately constant 

<img width="285" height="248" alt="Screenshot 2026-02-27 at 10 42 25 AM" src="https://github.com/user-attachments/assets/f13a2217-8535-4a0a-ac70-c25ff6936b37" />


**Observation**

The higher the gate voltage (VgsN), the larger the drain current for same drain voltage. The curves start at  origin and the saturation level increases with VgsN.

## PMOS IdsP vs VdsP Curve

<img width="214" height="274" alt="Screenshot 2026-02-27 at 10 43 16 AM" src="https://github.com/user-attachments/assets/2f966621-adb2-4718-99cb-1bb783aca315" />

Just like the NMOS, the PMOS also shows  family of curves for different gate-to-source voltages VgsP1 through VgsP5 (labelled as negative values -VgsP1 to -VgsP5). A more negative VgsP results in a larger magnitude of drain current.

## Comparing Both NMOS and PMOS Curves

<img width="466" height="257" alt="Screenshot 2026-02-27 at 10 44 31 AM" src="https://github.com/user-attachments/assets/b674950b-ff33-4f1f-b8b5-efa410c3d577" />

**Observations**

NMOS curves are in first quadrant — positive VdsN and positive IdsN

PMOS curves are in third quadrant — negative VdsP and negative IdsP

Higher |VgsN| gives higher IdsN value for NMOS; higher |VgsP| gives higher |IdsP| for PMOS .

---

# Day 2 Part 2 Lecture 4
# Step1 – Convert PMOS gate-source-voltage to Vin

## SPICE Simulation for Lower Nodes

By Observation:

VgsN = Vin – Vss = 'Vin'
VdsN = 'Vout'
VgsP = 'Vin – Vdd'
VdsP = 'Vout – Vdd'
IdsP = -IdsN

<img width="696" height="367" alt="Screenshot 2026-02-27 at 11 06 12 AM" src="https://github.com/user-attachments/assets/e7df02ba-4803-4003-a0a1-2f17fb68ef07" />

Let us assume the following values with Vdd = 2V:

<img width="231" height="183" alt="Screenshot 2026-02-27 at 11 08 37 AM" src="https://github.com/user-attachments/assets/4eb96417-36be-4479-abbe-398b246c4a10" />

we get vin from (Vin = Vgsp + Vdd):

<img width="260" height="186" alt="Screenshot 2026-02-27 at 11 10 18 AM" src="https://github.com/user-attachments/assets/6d784ebd-ebbb-409e-81ce-bb37a8f9b2a9" />

Since IdsP = -IdsN, the PMOS current curve is mirrored.
This is used to convert the PMOS Ids vs Vds curve to a form expressed in terms of Vin

<img width="417" height="173" alt="Screenshot 2026-02-27 at 11 12 57 AM" src="https://github.com/user-attachments/assets/c50df693-5840-4a18-897c-4a50e9ecc32f" />

<img width="464" height="378" alt="Screenshot 2026-02-27 at 11 14 05 AM" src="https://github.com/user-attachments/assets/8ee38f5d-16fa-480f-b673-ab8defc46871" />

used to convert the PMOS Ids vs Vds curve to a form expressed in terms of Vin

**Observations**

After conversion:
 When Vin = 0 → highest PMOS current curve
 
 When Vin = 0.5 → next curve
 
 When Vin = 1 → middle curve
 
 When Vin = 1.5 → lower curve
 
 When Vin = 2 → lowest PMOS current curve

---
#  Day 2 Part 2 Lecture 5
#  Step2 & Step3 – Convert PMOS and NMOS drain-source-voltage to vout

## Convert PMOS and NMOS Drain-Source Voltage to Vout

The PMOS IdsP Vs VdsP curve needs to be re-expressed in terms of Vout.

Step 2 — Convert VdsP to Vout

VdsP = Vout – Vdd. So the x-axis of the PMOS curve transforms as: Vout = Vdd + VdsP

<img width="538" height="227" alt="Screenshot 2026-02-27 at 11 24 01 AM" src="https://github.com/user-attachments/assets/471d2661-898a-45c6-be0c-350def9a139e" />

we replace -VdsP on x-axis with Vout using Vout = Vdd + VdsP. 

The result is the Load Curve for PMOS transistor plotted against Vout.

Step 3 — Obtain Load Curve for NMOS Transistor

To get the NMOS load curve, we use the equations and the NMOS IdsN Vs VdsN curve.

VdsN = 'Vout' — so x-axis is directly Vout

VgsN = Vin — so each curve corresponds to a specific Vin value

<img width="699" height="252" alt="Screenshot 2026-02-27 at 11 48 56 AM" src="https://github.com/user-attachments/assets/f2bcef90-f547-423a-9563-81064d7ec1b1" />

After applying the transformation Vout = Vdd + VdsP to PMOS curve, both NMOS and PMOS load curves are now expressed in terms of Vout on x-axis.

<img width="704" height="389" alt="Screenshot 2026-02-27 at 11 53 06 AM" src="https://github.com/user-attachments/assets/ffd194e4-c4d3-4536-bf8d-02f2cf30d3c6" />

The NMOS IdsN Vs VdsN curve is used directly — VdsN = Vout so it is already in terms of Vout

<img width="686" height="246" alt="Screenshot 2026-02-27 at 11 55 19 AM" src="https://github.com/user-attachments/assets/ae77dc54-b475-4c9a-a23a-2c88a53aa1e9" />

---

# Day 2 Part 2 Lecture 6

# Step4 – Merge PMOS – NMOS load curves and plot VTC

## Superimposing the Load Curves

Superimpose the Load curve of NMOS on the Load curve of PMOS.

<img width="590" height="231" alt="Screenshot 2026-02-27 at 1 14 29 PM" src="https://github.com/user-attachments/assets/eb7183fe-5e34-447e-8f60-17656ee70e54" />

Both PMOS and NMOS curves are now on same graph with Vout on the x-axis and IdsN on the y-axis. 

Each Vin value has one PMOS curve and one NMOS curve.

## Finding Intersection Points

Vin and Vout are common to PMOS and NMOS.

<img width="693" height="326" alt="Screenshot 2026-02-27 at 1 22 01 PM" src="https://github.com/user-attachments/assets/f2929585-8500-42ed-b2d2-8c6b7e1e4772" />

For each Vin value, the PMOS and NMOS curves intersect at a point. That intersection gives the operating Vout value for that Vin.
These are the points on the VTC.

## Plotting the VTC — Point by Point

**When Vin = 0:**

NMOS is OFF, PMOS is in linear region

Intersection happens at Vout = 2

First point plotted on VTC: (Vin = 0, Vout = 2)

**When Vin = 0.5:**

PMOS is in linear region, NMOS is in saturation
Intersection gives: 1.5 < Vout < 2
Second point plotted on VTC: (Vin = 0.5, Vout ~ 1.8)

**When Vin = 1:**

Both PMOS and NMOS are in saturation
Intersection gives: 0.5 < Vout < 1.5
Third point plotted on VTC: (Vin = 1, Vout ~ 1)

**When Vin = 1.5:**

PMOS is in saturation, NMOS is in linear region
Intersection gives: 0 < Vout < 0.5
Fourth point plotted on VTC: (Vin = 1.5, Vout ~ 0.3)

**When Vin = 2:**

NMOS is in linear region, PMOS is OFF
Intersection happens at Vout = 0
Fifth point plotted on VTC: (Vin = 2, Vout = 0)

<img width="694" height="387" alt="Screenshot 2026-02-27 at 1 31 52 PM" src="https://github.com/user-attachments/assets/396cc957-45f4-484b-ad88-4bc9662fe00c" />

---

# Day 3 part 1 Lecture 1
# SPICE deck creation for CMOS inverter

## SPICE Deck

**Step 1** – Component Connectivity

The CMOS inverter circuit consists of:

M1 — PMOS transistor connected between Vdd and output node.

M2 — NMOS transistor connected between output node and Vss (ground).

Both gates tied together as Vin input.

cload — load capacitor at output node to Vss.

<img width="215" height="311" alt="Screenshot 2026-02-27 at 1 38 33 PM" src="https://github.com/user-attachments/assets/02860c60-6b31-4c3f-89ae-b13d2dbe239d" />

**Step 2** – Component Values

The transistor dimensions and load capacitor values are added to the circuit:

M1 (PMOS) — W = 0.375u, L = 0.25u

M2 (NMOS) — W = 0.375u, L = 0.25u

cload = 10fF

Vdd = 2.5V

<img width="259" height="282" alt="Screenshot 2026-02-27 at 1 41 59 PM" src="https://github.com/user-attachments/assets/6714d22a-2a55-4f99-8ff5-8ddcba88a4d2" />

**Step 3** – Identify Nodes

Nodes are the connection points in the circuit. Each unique wire junction is assigned a node name. The nodes identified in this circuit are:

vdd — supply voltage node (top)
in — input node (Vin gate connection)
out — output node (drain junction of M1 and M2)
0 —  ground / Vss node

<img width="424" height="319" alt="Screenshot 2026-02-27 at 1 42 59 PM" src="https://github.com/user-attachments/assets/86c99a76-ab32-4f2d-b237-317e3b9ce0b4" />

**SPICE Netlist Syntax**

 <img width="361" height="100" alt="Screenshot 2026-02-27 at 1 44 00 PM" src="https://github.com/user-attachments/assets/b4aedff8-4538-4ad6-b22b-6560e998bce4" />

---

# Day 3 part 2 lecture 1
# Switching Threshold, Vm

## Comparing Two Device Configurations

Two SPICE simulations compared side by side:
Case 1: Wn = Wp = 0.375u, Ln,p = 0.25u   →   Wn/Ln = Wp/Lp = 1.5
Case 2: Wn = 0.375u, Wp = 0.9375u, Ln,p = 0.25u   →   Wn/Ln = 1.5, Wp/Lp = 3.75

<img width="675" height="321" alt="Screenshot 2026-02-27 at 1 54 40 PM" src="https://github.com/user-attachments/assets/0964d3cb-e8a4-4415-8b06-66eca063b740" />

Case 2 has a wider PMOS (Wp = 0.9375u) compared to Case 1 (Wp = 0.375u). 
This is done to match the drive strength of PMOS to NMOS, since the hole mobility of PMOS is lower than electron mobility of NMOS.

## Observations

Comparing both VTC curves:

**Case 1 (Wn/Ln = Wp/Lp = 1.5)** — switching threshold Vm ~ 0.98V, shifted slightly left (towards lower Vin)

**Case 2 (Wn/Ln = 1.5, Wp/Lp = 3.75)** — switching threshold Vm ~ 1.2V, shifted towards center (closer to Vdd/2)

Increasing Wp shifts the VTC to the right — makes the inverter switch at a higher Vin

## Static Behavior Evaluation – CMOS Inverter Robustness

**1. Switching Threshold, Vm**

Vm is the point where Vin = Vout on the VTC curve. It is found by drawing a diagonal line (Vin = Vout) on the VTC and finding the intersection.

<img width="572" height="376" alt="Screenshot 2026-02-27 at 1 57 49 PM" src="https://github.com/user-attachments/assets/57ca71c9-4d71-49f4-80da-c936b69e57f3" />

The diagonal line (Vin = Vout) is overlaid on the VTC curve. The point where they intersect is Vm — the switching threshold of the inverter.


<img width="657" height="272" alt="Screenshot 2026-02-27 at 1 57 17 PM" src="https://github.com/user-attachments/assets/77c43b9c-f71a-4bf3-9cdd-6d9d8ae7afc5" />

The intersection point differs between Case 1 and Case 2.

## Vm Values from VTC

 <img width="654" height="284" alt="Screenshot 2026-02-27 at 1 59 25 PM" src="https://github.com/user-attachments/assets/4d06ecef-8b7f-437d-9b7f-7113a0f8577e" />
 
<img width="492" height="237" alt="Screenshot 2026-02-27 at 2 00 00 PM" src="https://github.com/user-attachments/assets/fe791226-7bdd-433d-9f20-1a552268262f" />

From the VTC with all operating region labels:

PMOS linear, NMOS off   →   Vout = 2 (Vin ~ 0)

PMOS linear, NMOS sat   →   Vout ~ 1.8 (Vin ~ 0.5)

PMOS sat, NMOS sat   →   Vout ~ 1 (Vin ~ 1) — this is the transition region

PMOS sat, NMOS linear   →   Vout ~ 0.3 (Vin ~ 1.5)

PMOS off, NMOS linear   →   Vout = 0 (Vin ~ 2)

**Vm values:**

Case 1: Vm ~ 0.98V
Case 2: Vm ~ 1.2V

## Condition at Vm

<img width="543" height="291" alt="Screenshot 2026-02-27 at 2 01 30 PM" src="https://github.com/user-attachments/assets/21e06dd8-e543-4924-9eb5-ba2914a90541" />

**At the switching threshold Vm:**

Vgs = Vds for both PMOS and NMOS (since Vin = Vout = Vm at this point)

IdsP = -IdsN — the PMOS and NMOS currents are equal and opposite, confirming the equilibrium condition

Both transistors are in saturation at Vm

This condition (IdsP = -IdsN) is used to analytically derive the expression for Vm in terms of transistor parameters.

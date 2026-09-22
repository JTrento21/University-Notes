Lecture 1 - Transmission Media

What is transmission media?

Transmission media is whatever carries data from one device to another.

Data can travel as:

- Electric signals - copper cables
- Light - Fibre optic 
- EM waves - wireless communication

These are split into 2 main types:

- Guided media: The signal follows a physical path (twisted pair, coaxial cable, fibre optic)
- Unguided media: signal travels through space (radio, microwaves, infrared)

What limits communication?

You cannot send unlimited amounts of data through a communication channel. The main limitations are: 

- Bandwidth: The range of frequencies the channel can carry. Higher bandwidth generally transmit more data.
- Noise: Unwanted energy, signals mixed with intended signal
- Signal quality: The receiver must be able to distinguish the intended signal from interference.
- Physical characteristics of the medium: Different cables and wireless technologies behave differently.

Mental model:
Good communication = enough bandwidth + strong enough signal + low enough noise

Shannon's Theorem

Shannon's Theorem describes the theoretical maximum data rate of a noisy communication channel

C = Blog2​(1+S/N)

Where:
- C = Channel capacity in bits per second
- B = Bandwidth in Hz
- S = Signal power
- N = Noise power
The key idea is more important than memorising the maths immediately.

Increase bandwidth --> capacity increases
Improve signal-to-noise ratio --> capacity increases

Example: 
Bandwidth = 1MHz
S/N = 15

$$
C = 1,000,000×log_2​(16)
$$$$
log_2(16)=4
$$$$
C=4,000,000 bits/s
$$So the theoretical channel capacity is 4Mb/s

Transmission impairments

A signal leaving the transmitter does not necessarily arrive perfectly at receiver.

Basic model:
Transmitter --> Transmission Medium --> Receiver

Attenuation
Attenuation is the loss of signal strength over distance. The further a signal travels the weaker it generally becomes.

Examples: 

- Longer copper cables: More attenuation 
- Higher frequencies may experience greater losses
- Fibre also experiences attenuation

Distortion
Distortion is when the shape of the signal changes while travelling

Signals contain different frequency components, those frequencies may travel or be affected differently by the medium, causing the received by the medium causing the received signal to differ from transmitted signal.

Noise/Interference
Noise is unwanted signals that are added to the intended signals.

Examples:
- Thermal noise
- EM interference
- Crosstalk
- External interference

Why are Ethernet wires twisted?
Ethernet cables commonly contain twisted pairs of copper wires.

The twisting helps reduce:

- EM interference
- crosstalk between neighbouring wire pairs
Essentially, the geometry helps unwanted EM effects cancel out rather than consistently affecting one conductor.

So why are wires twisted in ethernet cables?
To reduce electromagnetic interference and crosstalk, improving signal integrity.

Electrical properties of transmission media

Copper network cables have electrical properties that affect how signals travel. 

Voltage: Volts, V
Electrical potential difference.

Current: Amperes, A
The flow of electric charge

Resistance: Ohms, Ω
Opposition to the flow of electrical current.
Greater resistance means more opposition to current. 

The water hose analogy describes Voltage as the Pressure, Current as the size of the hose, Resistance as sand inside the hose.

Ohm's Law
A fundamental electrical relationship:

V=IR

- V = Voltage
- I = Current
- R = Resistance

I=V/R
R=V/I

Resistance + inductance + Capacitance 
R + L + C

Inductance
A changing current creates a changing magnetic field. 

That magnetic field creates an effect that opposes changes in the current therefore Inductance resists rapid changes in current.

Unit: Henry, H
Symbol: L 

Capacitance
Capacitance describes the ability to store electric charge

In networking cables, capacitance influences how quickly voltage can change. Too much capacitance can affect high-frequency signals and therefore signal quality.

Unit: Farad, F

A cable is not just a piece of metal. Its resistance, capacitance and inductance influence how signals behave.

Transmission lines and impedance
At networking frequencies, cables behave as transmission lines.

Examples:
- Coaxial cable
- Twisted-pair cable
A key property is impedance

Impedance
Impedance describes how much the transmission medium opposes an alternating/changing signal.

Unit: Ohms, Ω

Impedance is not identical to resistance, resistance is part of the picture but impedance also accounts for effects such as capacitance and inductance.

Impedance matching reflections
A signal travelling down a transmission line a load

IF:
$$
Z_Load=Z_Line
$$The impedances are matched. The signals transfers efficiently into the load. If the impedances do not match, some energy may reflect back towards the transmitter. 

Its almost like an echo:
Signal travels forward --> impedance changes --> some signals reflects backwards.

Reflection coefficient
The reflection coefficient describes how much of the signal is reflected at an impedance boundary.

$$
Γ=Z_L​+Z_0/​Z_L​−Z_0​​
$$
- Z_L = Load impedance
- Z_0 = Characteristic impedance of the transmission line
- Γ = reflection coefficient

If:
$$
Z_L=Z_0
$$
$$
Γ=0
$$Meaning no reflection caused by impedance mismatch.

The conceptual point is more important than the equation.

Matched impedance --> Good signal transfer
Mismatched impedance --> reflections

Guided media - Coaxial Cable
A coaxial cable contains: 

Central copper conductor --> insulating dielectric --> surrounding conductor/shield

Older Ethernet standards included:

10BASE5: 10 Mb/s, Up to roughly 500 m

10BASE2: 10Mb/s, Up to roughly 185m

These are mainly historically important now, but they demonstrate how physical media constrain Ethernet implementations.

Guided media - Twisted Pair
Two insulated copper conductors are twisted together.
Typical insulated


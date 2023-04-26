The gate lead of a MOSFET is separated from the other leads by the gate
oxide layer which forms the gate of a MOS capacitor. For DC, this capacitor
should not pass any current. Thus, use the DMM in the resistance mode to
find the lead on the 2N7000 MOSFET which does not conduct to any of the
other leads, in either polarity.
With the gate lead identified, it stands to reason that the remaining leads
must be the drain and the source. The 2N7000 MOSFET happens to have a
special internal diode which guards against the drain being taken more
negative than the source, as shown in Fig. E3.1. (This situation can occur
during transient switching of an inductive load, and the internal diode is
present to protect against this.) The body of the MOSFET is also internally
connected to the source lead, effectively making the four terminal MOSFET a
three terminal part.

![[Pasted image 20230426111413.png]]
Switch the DMM to the diode test function and determine the source and drain leads from the direction that the transient protection diode allows current to pass (from source to drain). For the 2N7000 MOSFET, this also verifies that it is an n-channel device. More conventional MOSFETs which do not have either the transient  
protection diode or their body and source tied together (a true four-terminal MOSFET) would show the source and drain as symmetrical in so far as any DMM measurements are concerned. For such devices, the polarity of the body diode would be used to identify the body terminal and also whether the MOSFET was n-channel or p-channel.  
With all three leads of the 2N7000 MOSFET now identified, short the gate and source leads together with a small jumper wire on the solderless breadboard. This is to guarantee that VGS = 0. Use the DMM to measure the conduction from drain to source. If this is significant, then the device channel is turned on without any gate bias, and the MOSFET is a depletion mode (D-mode) or “normally-ON.” If the conduction from drain to source with VGS = 0 is negligible, then the MOSFET is an enhancement mode (E-mode) or “normally-OFF.” Make this determination for the 2N7000 MOSFET  and record the results in your laboratory notebook.

Can you rewrite the above measurement instruction in the way that easier for me to understand? 

To identify the gate lead of a MOSFET, use a DMM in resistance mode to find the lead that does not conduct to any other lead. The remaining leads are the drain and source. The 2N7000 MOSFET has an internal diode that protects against drain being more negative than the source. Use a DMM in diode test mode to determine the source and drain leads based on the direction that current flows through the internal diode (from source to drain). Short the gate and source leads together to ensure VGS = 0, then measure the conduction from drain to source. If it is significant, then the MOSFET is depletion mode or "normally-ON". If it is negligible, then it is enhancement mode or "normally-OFF". Record your results in your notebook.
# 2-Stage-OpAmp-Design-and-Layout-Implementation
The design and implementation of 2 stage operational amplifier using IHP 130nm open source PDK. The spice simulation is done using ngspice and xschem schematic designer and layout design is done using magic and klayout

# SCHEMATIC DESIGN

![Opamp Layout](Schematic_design_2_stage_opamp_white.png)

The schematic design of a two-stage CMOS operational amplifier developed using open-source EDA tools. The circuit consists of a differential input stage with current mirror load, followed by a common-source gain stage, and includes Miller compensation for stability. The design was implemented using the IHP SG13G2 130nm PDK with open-source tools such as Xschem for schematic design and Magic VLSI for layout implementation. This project helped me gain hands-on experience with analog circuit design, device sizing, biasing networks, and compensation techniques while working within a real semiconductor process design kit.

# TRANSIENT ANALYSIS

![Opamp Layout](Input_waveform_25mV_amplitude_white.png)



![Opamp Layout](Output_waveform_2V_rail_to_rail_amplitude_white.png)

The transient simulation results of a two-stage CMOS operational amplifier designed using the IHP SG13G2 130nm PDK. The first plot shows the differential input signal applied between IN1 and IN2, while the second plot shows the corresponding output response of the amplifier. The simulation was carried out using Xschem together with ngspice to verify the functionality and dynamic behavior of the circuit. This analysis helps validate the amplifier’s gain and response before proceeding to the physical layout implementation using Magic VLSI. Working through this process provided valuable hands-on experience in analog circuit design, simulation, and verification using open-source semiconductor design tools.

# AC ANALYSIS

![Opamp Layout](db_vs_frequency_plot_(magnitude_plot)_white.png)



![Opamp Layout](Phase_plot_(degrees)_white.png)

The AC analysis results of a two-stage CMOS operational amplifier designed using the IHP SG13G2 130nm PDK. The plots show the gain (magnitude) and phase response of the amplifier obtained through AC simulation. The magnitude response demonstrates a high DC gain with the expected roll-off at higher frequencies, while the phase plot provides insight into the amplifier’s stability and frequency behavior. The simulations were performed using ngspice with the schematic created in Xschem. Performing frequency-domain analysis like this is an essential step in analog IC design to evaluate gain, bandwidth, and stability before proceeding to layout implementation using Magic VLSI.

# NOISE ANALYSIS

![Opamp Layout](inoise_spectrum_curve_white.png)



![Opamp Layout](onoise_spectrum_curve_white.png)

The noise analysis results of a two-stage CMOS operational amplifier designed using the IHP SG13G2 130nm PDK. The plots show the input-referred noise spectrum and output noise spectrum across frequency. The results highlight the typical behavior where noise is higher at low frequencies due to flicker (1/f) noise and gradually decreases at higher frequencies. These simulations were performed using ngspice with the schematic designed in Xschem. Performing noise analysis is an important step in analog IC design, as it helps evaluate the noise performance and signal integrity of the amplifier before proceeding to layout implementation using Magic VLSI.

# POWER CONSUMPTION

![Opamp Layout](Power_Consumption_white.png)

The power consumption analysis of a two-stage CMOS operational amplifier designed using the IHP SG13G2 130nm PDK. The plot shows the instantaneous power drawn from the supply (VDD) during transient simulation, calculated from the product of supply voltage and current. This analysis was performed using ngspice with the schematic created in Xschem. Evaluating power consumption is an important aspect of analog IC design, as it helps ensure the amplifier meets power efficiency requirements while maintaining the desired gain and bandwidth performance before proceeding to physical layout using Magic VLSI.

# FFT PLOT

![Opamp Layout](FFT_plot_for_1Mhz_input_signal_white.png)

the frequency spectrum analysis of the output signal from a two-stage CMOS operational amplifier designed using the IHP SG13G2 130nm PDK. The plot shows the FFT (Fast Fourier Transform) of the output waveform, highlighting the dominant frequency components and harmonic content present in the signal. This analysis helps evaluate the spectral behavior and signal purity of the amplifier output. The simulations were performed using ngspice with the schematic created in Xschem. Performing frequency-domain analysis like this is useful for understanding distortion and harmonic components before moving forward with the physical layout using Magic VLSI.

#LAYOUT DESIGN 

![Opamp Layout](Magic_layout_1.png)



![Opamp Layout](Magic_layout_2.png)



![Opamp Layout](Magic_layout_3.png)



![Opamp Layout](klayout_1.png)



![Opamp Layout](klayout_2.png)





![Opamp Layout](klayout_3.png)

The custom layout implementation of a two-stage CMOS operational amplifier designed using the IHP SG13G2 130nm PDK with open-source EDA tools. The layout was created using Magic VLSI, following important analog layout practices such as device matching, symmetry in the differential pair, guard rings for substrate isolation, and careful routing of VDD and GND rails. The design was verified using open-source simulation tools including ngspice and schematic capture in Xschem. Working on this project provided valuable hands-on experience in translating an analog schematic into a physical layout while considering parasitics, device placement, and layout-driven performance in integrated circuit design.

# SPICE COMMANDS USED 

Transient Analysis:<br/>
tran 1n 10u<br/>
plot v(out)<br/>
plot v(in1,in2)<br/>

Bode Plot analysis:<br/>
ac dec 100 1 100T<br/>
plot db(v(out))<br/>
plot ph(v(out))*180/pi<br/>
plot phase(v(out))<br/>

Noise Analysis:<br/>
noise v(out) v2 dec 100 1 1G<br/>
//suppose if you are not getting inoise_spectrum or onoise_spectrum you can do the below steps<br/>
setplot<br/>
setplot noise1<br/>
display<br/>
plot inoise_spectrum<br/>
plot onoise_spectrum<br/>

FFT plot:<br/>
tran 1n 10u<br/>
fft v(out)<br/>
plot mag(v(out))<br/>


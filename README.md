# _**ACF for Different Line Codes**_
> ## _Project Description_
   * Software radio is the technique used to get the programmer's code as close to the antenna
as possible. It turns radio hardware problems into software problems. The fundamental
characteristic of software radio is that software defines the transmitted waveforms, and
software demodulates the received waveforms. This is in contrast to most radios in which
the processing is done with either analog circuitry or analog circuitry combined with
digital chips.
> ## _Block Diagram_
![Block Diagram](https://user-images.githubusercontent.com/67025780/230783773-4174e52e-9d23-4bc8-9a6e-3d2b5ba25923.jpeg)

> ## _Project Goal_
* To transmit sequence of data in terms of symbols (7 bits per symbol) with different line codes, we used three line codes
    * Polar NRZ
    * Unipolar NRZ
    * Polar RZ
* Then get mean and ACF for each one, then PSD to determine bandwidth of transmitted signal.

> ## _Contents_
   * _MATLAB file (.mlx)._
   * _Result Figures._

> ## _Result Figures_
1. Polar NRZ
![Stati_ACF_Polar_NRZ_10000_ensemble](https://user-images.githubusercontent.com/67025780/230783949-e6913b3d-3675-4697-acdd-6943dc183663.png)



2. Unipolar NRZ



3. Polar RZ


> ## __Change Line Code__
* To change which line code to use, change variable ``choose`` to any value from {1 to 3}
```MATLAB
    %%%%%%%% change this line according to line coding %%%%%%%%
choose = 1;                                   % choose which line code to use (1. polar NRZ, 2. unipolar NRZ, 3. polar RZ)
switch choose
    case 1
        data=(2*data-1)*A;                          % mapping to A & -A (Polar NRZ)
        data=repmat(data, number_of_samples, 1);    % repeat each bit 7 times to sample DAC every 10ms
    case 2
        data=data*A;                                % mapping to A & 0  (Unipolar NRZ)
        data=repmat(data, number_of_samples, 1);    % repeat each bit 7 times to sample DAC every 10ms    
    case 3
        data=NR_line_code(data, A, number_of_bits); % mapping           (Polar RZ)
    otherwise
        disp("invalid line code choose");
end
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```



# Audapter
Audapter is a software package for configurable real-time manipulation of acoustic parameters of speech that runs on general-purpose computers. It is designed for research on auditory-motor interactions in speech production, but may also be of use for certain speech signal processing applications. The current version of Audapter supports manipulation (i.e., perturbation) of the following acoustic parameters:
1. Formant frequencies (F1 and F2), in both static and time-varying ways
2. Fundamental frequency (F0, or pitch)
3. Local timing, through time-warping
4. Local intensity
5. Global time delay (delayed auditory feedback)
6. Global intensity

This is the MEX core of the MATLAB package. Clone this whole repository if you want to make programmatic changes to the Audapter program itself. If you just want to run Audapter, follow the Setup instructions below.

# Setup to use Audapter
1. Download the compiled .mex file from the ["Releases" section of this repo](https://github.com/blab-lab/audapter_mex/releases), and add it to your MATLAB path. Run `Audapter('version')` in the MATLAB Command Window and verify that it shows the version listed on the Releases section of this repo.
2. Download the accompanying repository for MATLAB files from [blab-lab/audapter_matlab](https://github.com/blab-lab/audapter_matlab) and add it to your MATLAB path. You must use the blab-lab fork of audapter_matlab if you are using the blab-lab fork of audapter_mex.
For more info on using Audapter, see the Documentation section below.

## Special setup for Audapter versions b2.4 and older (before July 2026)
If you are intentionally using Audapter version b2.4 or older, you will also need to download and add to your MATLAB path the [blab-lab/commonmcode repository](https://github.com/blab-lab/commonmcode). Then, move the commonmcode folder to the bottom of your MATLAB path. The commonmcode repository is not used at all for Audapter version b2.5 (July 2026) or later.

## Audio interfaces and Focusrite drivers
The Audapter built-in demos (such as `audapterDemo_online.m`) assume you are using a Focusrite device. If you are using a different device, you will need to edit the command `Audapter('deviceName', ...)`. For MOTU devices, the device name will be 'MOTU MicroBook'. 

Focusrite (e.g., Scarlett) Generation 4 devices do not work with Audapter. Generation 1, 2, and 3 Focusrite devices are supported. Additionally, you must use the Focusrite driver version 4.65.5. This driver works on all Windows operating system versions. Newer Focusrite drivers cause MATLAB to crash when Audapter tries to take control of the device, (ie, when it `'Start'`s). Download drivers from [Focusrite's website](https://downloads.focusrite.com/focusrite).

## Troubleshooting
1. **Operating system**.  Audapter does not work on Mac. It is confirmed to work on Windows 10 and 11, and it should work on 8 and 7.
2. If you have multiple files with the same name on your MATLAB path, MATLAB will only pick one to use. Enter `which [function-name] -all` in the MATLAB Command Window to see all instances of [function-name] on the MATLAB path. Or run `which Audapter -all` to search for all instances of the .mex file.
3. The Audapter built-in demos assume your Current Folder is the audapter_matlab/example_data folder.
4. Here is a simple script to test if Audapter can start properly:
```
p = getAudapterDefaultParams('male');
AudapterIO('init', p)
disp('Initialized successfully');
Audapter('deviceName', 'Focusrite USB');
Audapter('start')
Audapter('stop')
disp('Started and stopped successfully');
```
For further technical support, contact Chris Naber (cwnaber@wisc.edu).

# Documentation
* [Audapter Manual](https://sites.bu.edu/guentherlab/files/2022/09/AudapterManual_2.1.5.pdf) for build instructions and further information.
* See also [Audapter: Beyond the Manual](https://kb.wisc.edu/smng/110902) for features specific to the blab-lab fork

# Acknowledgements
The following individuals participated in the writing of Audapter (in alphabetical order of last name):
* Marc Boucek
* Shanqing Cai
* Satrajit Ghosh
* Kevin Reilly
* Virgilio Villacorta
  
The current maintainer of this project is:
* Shanqing Cai
    
The blab-lab/audapter_mex fork of Shanqing's Audapter contains additional programming by:
* Ben Parrell
* Chris Naber
* Carrie Niziolek

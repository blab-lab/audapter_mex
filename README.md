# Audapter C++ MEX Code
Audapter: Real-time speech signal perturbation (formant frequencies, pitch, timing and intensity). This is the MEX core of the MATLAB package. Clone this whole repository if you want to make programmatic changes to the Audapter program itself.

If you just want to run Audapter, the compiled .mex file is the only thing from this respository that you need. Download it from the ["Releases" section of the GitHub page](https://github.com/blab-lab/audapter_mex/releases), and put it somewhere on your Matlab path. See below for additional setup to run the blab-lab fork of Audapter.

## Setup to use Audapter
1. Download the compiled .mex file from the ["Releases" section of this repo](https://github.com/blab-lab/audapter_mex/releases), and add it to your MATLAB path. Call `Audapter('version')` from the Command Window and verify that it shows the version listed on the Releases section of this repo. 
2. Download the [blab-lab/audapter_matlab](https://github.com/blab-lab/audapter_matlab) repository and the [blab-lab/commonmcode repository](https://github.com/blab-lab/commonmcode) and add them to your MATLAB path. You must use the blab-lab fork of these repositories if you are using the .mex file from this blab-lab/audapter_mex repository.

### Optional but recommended setup
1. In your MATLAB path, move the commonmcode folder to the bottom. This will preserve the MATLAB default spectrogram color settings
2. If you are using a Focusrite device for recording, such as a Focusrite Scarlett 2i2 (any generation), only certain driver versions will work. **You must use version 4.65.5** on Windows 10 or 11. More recent Focusrite driver versions cause Audapter to crash when it tries to take control of the device, (ie, when it `'Start'`s). Download driver versions from [Focusrite's website](https://downloads.focusrite.com/focusrite).
3. The Audapter built-in demos (such as `audapterDemo_online.m`) assume you are using a Focusrite device. If you are using a different device, you will need to edit the command `Audapter('deviceName', ...)`. For MOTU devices, the device name will be 'MOTU MicroBook'. 

### Troubleshooting
1. **Operating system**.  Audapter does not work on Mac. It is confirmed to work on Windows 10 and 11, and should work on 8 and 7.
2. Make sure you only have one version of files on your MATLAB path. Enter `which [function-name] -all` in the MATLAB Command Window to verify which files are on your path.
3. The Audapter built-in demos assume your Current Folder is the audapter_matlab/example_data folder.
4. Here is a simple script to test if Audapter can start properly:
```
Audapter('deviceName', 'Focusrite USB');
p = getAudapterDefaultParams('male');
AudapterIO('init', p)
Audapter('start')
Audapter('stop')You don't need to change
```

## Resources
* [Audapter Manual](https://sites.bu.edu/guentherlab/files/2016/11/AudapterManual.pdf) for build instructions and further information.
* SEE ALSO: [Audapter: Beyond the Manual](https://kb.wisc.edu/smng/110902) for functionality specific to the blab-lab fork
* Audapter MATLAB Code: https://github.com/blab-lab/audapter_matlab
   
## Acknowledgements
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

# How to start with SGX:

please note that:
you must have CPU which support SGX 


## BIOS setting

depending on the motherboard model, you need to change the setting of the BIOS setting in the way that SGX is enabled. please note that, the last version of SGX only support Windows and Linux distributions (and not MacOS).  Rest of document is based on Windows 10 installation.

## Installing visual Studio 

The last version that SGX' SDK support now is 2017. Therefore, you can either use 2015 edition or 2017 edition. It is important to install Visual Studio before SDK.

## Installing Intel SGX SDK

Depending on the version of the Visual Studio check the **integration** and **debugging** for the Visual Studio. 
you can find the SDK for Windows and Linux [Here](https://software.intel.com/en-us/sgx/sdk)

## Check the SGX

Open Visual Studio in administration mode.
Set the debugger on SGX debugger.
run SampleSGXEnable program 

you should see:
`" SGX device has been enabled "` 

If there is any thing else first handle the error that is been shown on the screen.
# Installing Intel® SGX SSL library 

The Intel® Software Guard Extensions SSL (Intel® SGX SSL)  ([link](https://github.com/intel/intel-sgx-ssl)) cryptographic library is intended to provide cryptographic services for Intel® Software Guard Extensions (SGX) enclave applications. The Intel® SGX SSL cryptographic library is based on the underlying OpenSSL* Open Source project, providing a full-strength general purpose cryptography library.

## Windows

Before biulding the library you need to install the followings: 
- Microsoft Visual Studio 2015 or 2017 
- 7-Zip
- Perl (in my case the installing was only working when I was using the Strawberry version)
- NASM (Netwide Assembler)
- Intel(R) SGX SDK.
- Intel(R) SGX SDK.

7-Zip, Perl, NASM need to be included in machine's **PATH variable**.
	  For adding them to path variable you need to do the following steps.
	  
	1- search for environment variables in the search bar for windows 
	2- click in the advance tab select Environment Variables 
	3- On system variables double tab on path and click on the new button 
	4- Add the pass for 7-Zip (the installation path) ( you only need to type the path not the .exe file. For example if 7-Zip is on the "C:\Program Files \7-Zip\7z.exe" you just need to add "C:\Program Files \7-Zip" to the path 
	5- Do the same thing for Perl, NASM

Now you can start installing the SSL library. For installing the library you need to the the following steps:


### 1- Download OpenSSL package

Download and unzip Intel SGX SSL library ([link](https://github.com/intel/intel-sgx-ssl)) on the folder you will find a openssl_source folder. Download OpenSSL ([link](https://www.openssl.org/source/)) but don't unzip it, and copy OpenSSL zip file in the openssl_source folder. As I understand this library works with version 1.1.0 and above. 

### 2- Download and install latest SGX SDK

Install Intel SGX SDK ([link](https://software.intel.com/en-us/sgx/sdk)), there is a guide from Intel but I have also uploaded a guide for installing the SDK which can be found [here](https://github.com/Behnam-Shobiri/SGXSSL-lib/blob/master/QuickStart/How_To_Start_With_SGX.md) 

### 3- Build the library 
Go back to the Intel SGX SSL and then go to the Windows folder you will find a  build_all.cmd  you can run it with cmd to see the errors.
in order to build the library please specific the version for open ssl 
```
build_all.cmd <OPENSSL_VERSION>
```
( for example if you download the Openssl-1.1.1d.tar.gz you need to  	
write
```
build_all.cmd  openssl-1.1.1d 
```
Please note that the default version is openssl-1.1.1 

## Microsoft Visual Studio 
I have not try installing with different versions of Microsoft Visual Studio, However I found a bug in the 2017 community version. If you have same problem please let me know. Nonetheless, you may have the same problem as the the 2017 community version so try the solution.   

### Microsoft Visual Studio 2017 community version 
Intel SGX SSL library was supposed to support the 2017 version as well; however, for some reason they only support the professional version (at least for now or maybe there was problem in their code and they forgot to add community version). In order to solve the problem with the community version you need to open the build_package.cmd file (with a notepad or any other editor) and find this line 
```
  call "C:\Program Files (x86)\Microsoft Visual Studio\2017\Professional\VC\Auxiliary\Build\vcvarsall.bat" %VS_CMD_PLFM%
 ```
 
Just change the Professional to Community on the line (or if you change the path yourself change it to that) 


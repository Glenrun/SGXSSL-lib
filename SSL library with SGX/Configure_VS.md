
# Configuring Visual Studio for Intel® SGX SSL library

Intel® Software Guard Extensions SSL Developer Guide [1]

If you already have a basic application and an enclave project, to use the Intel® SGX SSL library in an Intel® Software Guard Extensions (Intel® SGX) application project, follow the listed steps:

- In visual studio you will need to do the following (assuming you already have basic App + Enclave project):
	 ``` 
	 if you don't have any project you can simply use the "SampleEnclave" project which can be found in SDK as test project
	```


-   As a start, you may extract Intel® SGX SSL package to solution’s directory. (You may also extract it into Intel® SGX SDK directory, or any other location, as long as you refer to the right location in projects’ settings)

-   In your EDL file add:
   from "sgx_tsgxssl.edl" import *;
	   ```  
	   This file can be found in either the App or Enclave on 
	   the src directory
	   ```

-   In the **Enclave** project (do these steps to all of your build environments):

	-   Select **Properties->Linker->Input->Additional Dependencies:**
	    Add ‘‘libsgx_tsgxssl_crypto.lib; libsgx_tsgxssl.lib;’’
	    ```
	      In this part we are declaring the lib files that 
	      we want to use (in this case the two lib files
	      that are sepreated with ; 
	      ```
	   -   Select **Properties->Linker->General->Additional Library Directories:**
	   Intel® Software Guard Extensions SSL Developer Guide
	 Add the folder where you placed the libraries, (you better use the 	built in macros like \$(SolutionDir)\$(Platform)\\$(Configuration)\ 	etc. so you can control the different builds)
			```
			In this part, we are adding the path that 
			.lib files exit on. usually, they are in the path
			that you extract them in the lib folder and the
			rest depends on your configuration (32 or 64 and
			debug or release) just the path to the file is
			enough you don't need to add the
			file name at the end.
			```

		-   To add the folder where you placed the EDL file, right click your EDL file, then select
 **Properties->Custom Build Tool->Command Line:**  
  Add the EDL file path to the ‘--search path’ separated with ‘;’
 ``` EDL file path is on the extracted path for library in the include folder.```

	-   Select **Properties->C/C++->General->Additional Include Directories** and add the folder where Intel® SGX SSL header files are located. (<path to the package>\include)
 ``` This path is on the extracted path for library in the include folder.```			


-   In the **Application** project, use the following steps to set up the environment for the Intel® SGX SSL library:
		-Intel® Software Guard Extensions SSL Developer Guide

	-   Select **Properties->Linker->Input->Additional Dependencies:** Add ‘‘libsgx_usgxssl.lib;Ws2_32.lib’’
	 ```
	      In this part we are declaring the lib files that 
	      we want to use (in this case the two lib files
	      that are sepreated with ; 
	   ```

	-   Select **Properties->Linker->General->Additional Library Directories:**  
    Add the folder where you placed the libraries (you better use the built in macros like \$(SolutionDir)\$(Platform)\\$(Configuration)\ etc. so you can control the different builds)
    ```
		In this part, we are adding the path that 
		.lib files exit on. usually, they are in the path
		that you extract them in the lib folder and the
		rest depends on your configuration (32 or 64 and
		debug or release) just the path to the file is
		enough you don't need to add the
		file name at the end.
	```
	-   To add the folder where you placed the EDL file, right click your EDL file, then select **Properties->Custom Build Tool->Command Line:**  
    Add the EDL file path to the ‘--search path’ separated with ‘;’ ``` EDL file path is on the extracted path for library in the include folder.```

	-   If your project does not use Intel compiler, add the path to the Intel compiler libraries through **Properties->Linker->General->Additional Library Directories**
	 ``` This path is on the extracted path for library in the include folder.```	

## References 
[1]  “Intel® Software Guard Extensions SSL (Intel® SGX SSL) Library.” _Github_, github.com/intel/intel-sgx-ssl/blob/master/Windows/package/docs/Intel(R)%20Software%20Guard%20Extensions%20SSL%20Library%20Windows%20Developer%20Guide.pdf.

# OpenCV-for-iOS
This repository has a pre-built version of OpenCV for iOS builds. 
Only iOS 11+ supported.

OpenCV is only available in C++ and Python. Moreover OpenCV needs to be built specifically for iOS development in C++.
Luckily for us, I have already built the Xcode library, so we don’t need to repeat it! 

For those of you who are interested in the build process, there is a step-by-step tutorial for that in `OpenCV for iOS Development Tutorial.pdf` in this repository.

# Steps to setup OpenCV in Xcode

1. Extract the zip file as `opencv2.framework` \
**NOTE - If the standard zip extractor does not work, please install 7zip on your machine to expand the zip file.**

2. You can add the OpenCV library in Xcode with a simple drag-and-drop action on the opencv2.framework folder.
It will give you a pop-up when you do so, keep the settings given below:
            
3. OpenCV is now added in the project modules.

# Bridging headers

- For you to use OpenCV in C++, you need to run it through Objective-C.
- [Apple documentation](https://developer.apple.com/documentation/swift/importing-objective-c-into-swift) gives detailed instructions on how to import Objective-C code in Swift.
- Using "Bridging Headers", you can directly expose the Objective-C functions to be accessible in Swift.
- Make sure to `#include` the headers of the individual Objective-C files in the Bridging Header.

# Make Objective-C compatible with C++

- Standard Objective-C (`.m`) still cannot directly run C++ code, as it is compiled differently.
- You can add C++ compatibility by simply changing the file name from `.m` to `.mm`. In a way, it becomes an an Objective-C++ file!

# How does C++ code work in iOS?

- You may be able to run C++ through the Objective-C code, but you cannot access it directly in your Swift project.
- This is why you should keep your computation in C++, convert your data to Objective-C compatible data types and return those.
- Similarly, your Objective-C header should also have only standard Objective-C compatible declarations.

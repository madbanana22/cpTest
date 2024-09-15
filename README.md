# Cross-Platform: The Test
###### (wow it feels really overexagerrated)

This application serves as an example of a really simple cross-platform C++ app (this one is a calculator).

# The Idea

<p align="center">
  <img alt="frontend is an exe, backend is a lib linked to it" src=".github/ideaMain.png" width="45%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="frontend provides a sweet unified api for the backend instead of stinky platform specific ones (hi windows.h)" src=".github/ideaLibs.png" width="45%">
</p>

# Compile instructions
## Prerequisites
1. CMake
2. A generator (MSBuild, Ninja, Make, etc)
3. A compiler (MSVC, Clang, GCC, etc)
   - Note: Android supplies its own compiler toolchain redistributed as the Android NDK
   - [Very helpful tutorial explaining how to install the Android NDK toolchain for CMake](https://google.com/search?q=how+to+install+android+ndk+toolchain+for+cmake)
4. Click on a frontend you would like to build for 🔽
## Frontends
| Frontend | Platforms | LOI | Description | Build system |
|----------|-----------|:---:|-------------|--------------|
| [Terminal](https://github.com/madbanana22/cpTest_terminal) | Anything with a terminal | 🚧 | Uses, well, a terminal for communicating with the program. | CMake |
| [Android](https://github.com/madbanana22/cpTest_android) | Android | ❌ | Uses Android UI, kind of functions as a normal calculator. | Android Studio |

**LOI stands for "Level of Implementation"**  
| Icon | Meaning |
|:-:|:--|
| ❌ | Not Implemented |
| 🚧 | Work in Progress |
| 🐛 | Implemented, but broken |
| ✅ | Implemented |

# FAQ
**Q:** I tried to CMake this repo, it only compiled a library. WTF??  
**A:** Read the compile instructions.

**Q:** I want to make a closed source project based on this.  
**A:** This code is licensed under the MIT license. Do whatever the hell you want with it lol I don't care

**Q:** I want to make a frontend for my toaster. How?  
**A:** First, be sure of a couple of things:
- You have access to the SDK used to build apps for your toaster
- It is possible to run your program on your toaster
  - (does it rely on an API provided by your OS that is not a thing on your toaster?)
  - (will your toaster blow up if you try to run it? (is your toaster beefy enough to run your app?))
  - (does it rely on a third party lib that was not ported to your toaster?)
- Said SDK allows using C libraries
  - if it does not, but still uses C/C++ that's no problem - just embed the backend into your program
  - (note that this sample project is build around C++, C here is used only for communicating between C++ and another language like god forbidden Java)
- You don't have any suicidal thoughts (if working for Android) <!-- screw you android studio !-->

Now here's the basic process of building a frontend:
1. Take a look at the backend. Think of a way to realise it on your toaster.
2. Link your backend to the frontend.
3. Provide the functions needed to run it.

Think of it as if you were designing a thunderbolt (backend) to 3.5mm jack adapter (frontend). Fundamentally different things that you need to somehow link together.
<!-- yes i'm terrible at explaining things. no i don't give a shit. !-->

**Q:** Do I have to update every frontend after making a tiny change??  
**A:** Mostly, no. If you do need to add a big feature that requires some new API that you did not yet add to your project, you will need to update each frontend to include that API.  
  - If you do need to update each frontend because you need to make a tiny change, you are probably going the wrong way.  
  - Your frontend should ONLY supply libraries, handle calls to the OS, maybe sometimes manage UI and THAT'S IT.  
  - If your frontend is doing more work than the backend, you might as well develop for each platform separately.

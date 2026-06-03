# Installing_GODDeSS
Repository for installing GODDeSS framework at Geant4 v.10.05.0

## Installing Geant4 v. 10.05.0
If you are using modern versions of Cmake, you need to modify some clases.
For cmake 3.28.3 and gcc 13.3.0 you need to modify 2 files in order to compile Geant4

First, open ```G4tgrEvaluator.cc``` using a text editor:
```bash
nano /home/user/geant4-v10.5.0/source/persistency/ascii/src/G4tgrEvaluator.cc
```
then, go to line:
```c++
G4double fsqrt( G4double arg ){  return std::sqrt(arg); }
```
and modify ```c++ fsqrt``` into ```c++ g4_fsqrt``` so it looks like:
```c++
G4double g4_fsqrt( G4double arg ){  return std::sqrt(arg); }
```

Second, in the same file, go to line:
```c++
setFunction("sqrt", (*fsqrt));
```
and modify ```c++ *fsqrt``` into ```c++ *g4_fsqrt``` so it looks like:
```c++
setFunction("sqrt", (*g4_fsqrt));
```

This project is currently made of TraceSurfer, a self-modifying code analyzer coming with an IDA add-on.

It can:
  * generate trace of memory references
  * import these traces in the popular IDA Pro disassembler and tag the disassembled code with runtime information
  * generate graphs showing a high-level analysis of the self-modifying behavior, useful for malware analysis

### Getting Started ###
  1. download and install the latest Pin kit for your system from http://www.pintool.org (a pre-built binary is included for Pin v33586 for Windows)
  1. unzip the archive in %PIN\_HOME%\source\tools
  1. (optionally) download and install pydot if you want to generate graphs

You can now build TraceSurfer from source or run the following command to trace any executable:
```
tracesurfer [options] -- <binary>
```

A trace file will be generated (binary.trace.out), that can be imported in IDA Pro (known to work with version 5.5) or analysed with the following command:
```
python utils\tracesurfer.py binary.trace.out
```

To import a trace file in IDA:
  1. open the traced binary in IDA
  1. press alt-9 to run the utils\ida-tracesurfer.py IDAPython script
  1. select the trace file to open
  1. wait and see

### How to build from source ###
The following is known to work with Microsoft Visual C++ 2008 Express Edition:
  1. open the Visual Studio 2008 Command Prompt
  1. go to directory %PIN\_HOME%\source\tools\TraceSurfer
  1. if you are on an x64 system and want to build a 32-bit pintool, run
```
set TARGET=ia32
```
  1. run
```
..\nmake
```
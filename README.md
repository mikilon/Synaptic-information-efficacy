# Synaptic-information-efficacy
Matlab/Java code for entropy and mutual information estimation between spike trains based on CTW algorithm

 SIE estimation using the CTW algorithm Mickey London
(mikilon@gmail.com)                     Jan 11, 2010

 The latest version of the algorithm can be found as well as at: www.mikilon.org/Code For more info about SIE and the CTW algorithm see:
London, M, Schreibman, A, Hausser, M, Larkum, ME and Segev, I (2002) The information efficacy of a synapse. Nat. Neurosci. 5(4):332-40.

This package contains a bunch of Java programs to compute entropies and mutual information between spike trains. The easiest way to start is using matlab, however one can use the code directly via a shell interface. As the package is written in Java it is platform independent and can ran on Mac OS X (tested), Windows XP (tested) and probably on any machine that has Java installed (not tested).
Quick start (matlab):
1. Download the package and store it in a folder of your choice. I assume here that this is: /Users/mickey/matlab/CTW/
2. Setting matlab to recognize the java code and the matlab functions.
Matlab has a virtually transparent interface with Java classes. This makes it possible to use the Java code as if it is a native matlab code. There is however one necessary step. Matlab should know where the classes are, so we need to modify the classpath. In matlab type:
edit([matlabroot '\toolbox\local\classpath.txt'])
3. Add three lines at the bottom of the file (replacing the prefix: /Users/mickey/ matlab/CTW/Java with the true location on your system): /Users/mickey/CTW/Java/mpjava/src
/Users/mickey/CTW/Java
      /Users/mickey/CTW/Java/Helpers
and save it.
4. Restart matlab (This is unfortunately necessary for matlab to reread the classpath.txt file, but from now on you can forget about it, that is until you install a new version of matlab)
5. Add the folder
      /Users/mickey/CTW/matlab
to your matlab path (use from matlab desktop File->Set path).
6. Test it: in matlab write:
      >> s = [5 23 28 41 50 63 73 77 82 85 88 89 99 103 118 127 130 142
      149 155];
      >> entropy_ctw(s,0,160,2,10)
  
       ans = 423.6299
Check out the the other functions using:
>>help  mutual_information_ctw
for example you can test it by:
>> s1 = s+rand(size(s));
>> [mi,h,ch,chshuffle] = mutual_information_ctw(s,s1,0,150,2,15,0)
and similarly
>> help conditional_entropy_ctw
Non matlab use:
The java classes can be used directly from the shell or from shell script. For that the $CLASSPATH system environment variable should be set to include the three folders mentioned above (the Java folder of the package, the mpjava/src and the Helpers). Note that mac, and unix are using different syntax to define CLASSPATH than windows.
Check out the file
running_from_shell_example.csh
for an example and more details.

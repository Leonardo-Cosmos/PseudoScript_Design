TestIntegration framework is design to separate logic of test case, implementation of test automation module and concrete environment configuration.
A series of interfaces are defined, and implementation are provided to support base function.

1. Step
Step is a simple module of in test flow. It can be implemented as an atomic step or an collection of existing steps. As reusable module, step contains neither environment configuration nor test data.
StepAssembly is compiled file of Step classes. For Java, it's JAR. For .Net, it's DLL.

2. StepInfo
StepInfo is abstract description of Step. StepInfo is used to write logic of test case. According to parameter list of Step, argument list should be assigned.

3. Script
Usually, test case is running in a system other than the one in which it is written. Therefore, test case is a kind of data being transfered from provider (ScriptProvider) to consumer (ScriptConsumer). Script is a wrap of StepInfo list that is suited to transfer from one system to another.

4. StepDetector
Because test case is written independent of executable code, available StepInfo set should be defined for edit assistance and validation. Definition is a XML file, so it can be manually created and modified. To make this easy, developer may add specified mark in source code, and StepDetector will generate StepInfo definition file by checking StepAssembly.
(For Java, mark is annotation. For .Net, mark is attribute.)

5. DataSource
DataSource is a container of test data, in which test data is stored as key-value pair.

6. Case is executable version of script. Therefore test data is filled in and steps are composited.

7. Invoker
Invoker accept case instance and invoke steps. By that, test case is really executed.
Environment configuration is handled here.

8. Reporter
Invoker just run test case and return test result. However, appropriate format is necessary to generate reasonable and readable test report. In addition, sometimes test result is collected to another system such as database. Reporter is a channel of test result from Invoker to desired destination.

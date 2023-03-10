# SLNF file fails to build for valid paths

Repro instructions:

1. Clone this repo on a Linux machine to a path containg an "@" sign.
2. Try to build using the solutions filter.

```sh
git clone https://github.com/handerss-tibco/SlnfFails.git SlnfFails@1
cd SlnfFails\@1/
dotnet build SlnfFails.slnf
```

The following error occurrs:

```
The build stopped unexpectedly because of an internal failure.
System.IO.DirectoryNotFoundException: Could not find a part of the path '/home/handerss/repos/SlnfFails%401/SlnfFails.sln'.
   at Interop.ThrowExceptionForIoErrno(ErrorInfo errorInfo, String path, Boolean isDirectory, Func`2 errorRewriter)
   at Microsoft.Win32.SafeHandles.SafeFileHandle.Open(String path, OpenFlags flags, Int32 mode)
   at Microsoft.Win32.SafeHandles.SafeFileHandle.Open(String fullPath, FileMode mode, FileAccess access, FileShare share, FileOptions options, Int64 preallocationSize)
   at System.IO.Strategies.OSFileStreamStrategy..ctor(String path, FileMode mode, FileAccess access, FileShare share, FileOptions options, Int64 preallocationSize)
   at System.IO.Strategies.FileStreamHelpers.ChooseStrategy(FileStream fileStream, String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, FileOptions options, Int64 preallocationSize)
   at System.IO.File.OpenRead(String path)
   at Microsoft.Build.Construction.SolutionFile.GetSolutionFileAndVisualStudioMajorVersions(String solutionFile, Int32& solutionVersion, Int32& visualStudioMajorVersion)
   at Microsoft.Build.Execution.ProjectInstance.LoadSolutionForBuild(String projectFile, PropertyDictionary`1 globalPropertiesInstances, String toolsVersion, BuildParameters buildParameters, ILoggingService loggingService, BuildEventContext projectBuildEventContext, Boolean isExplicitlyLoaded, IReadOnlyCollection`1 targetNames, ISdkResolverService sdkResolverService, Int32 submissionId)
   at Microsoft.Build.Execution.BuildManager.LoadSolutionIntoConfiguration(BuildRequestConfiguration config, BuildRequest request)
   at Microsoft.Build.Execution.BuildManager.HandleNewRequest(Int32 node, BuildRequestBlocker blocker)
   at Microsoft.Build.Execution.BuildManager.<>c__DisplayClass98_0.<IssueBuildRequestForBuildSubmission>g__IssueBuildSubmissionToSchedulerImpl|1(BuildSubmission submission, Boolean allowMainThreadBuild)
```


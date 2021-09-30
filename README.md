# Repro for Gradle dependency verification Android Studio Gradle sync failure

## Repro steps

1. Open this project in Android Studio (tested with Linux `2021.1.1 Beta 1`)
2. Select "Sync Project with Gradle Files"

### Expected
Success

### Actual
Failure, Android Studio Gradle sync fails with:
```
Failed building KotlinMPPGradleModel
org.gradle.api.internal.artifacts.verification.DependencyVerificationException: Dependency verification failed for junit:junit:4.12:
  - On artifact kotlin-test-junit-1.5.31.module (org.jetbrains.kotlin:kotlin-test-junit:1.5.31) in repository 'maven': checksum is missing from verification metadata.

If the artifacts are trustworthy, you will need to update the gradle/verification-metadata.xml file by following the instructions at https://docs.gradle.org/7.4-20211026220137+0000/userguide/dependency_verification.html#sec:troubleshooting-verification

These files failed verification:
  - GRADLE_USER_HOME/../../../../../../ssd/ssd1/temp/gradle-bug-crash-android-studio-sync/repo/org/jetbrains/kotlin/kotlin-test-junit/1.5.31/kotlin-test-junit-1.5.31.module

GRADLE_USER_HOME = /usr/local/google/home/aurimas/.gradle

These files failed verification:
  - GRADLE_USER_HOME/../../../../../../ssd/ssd1/temp/gradle-bug-crash-android-studio-sync/repo/org/jetbrains/kotlin/kotlin-test-junit/1.5.31/kotlin-test-junit-1.5.31.module

GRADLE_USER_HOME = /usr/local/google/home/aurimas/.gradle

Open this report for more details: file:///ssd/ssd1/temp/gradle-bug-crash-android-studio-sync/build/reports/dependency-verification/at-1635301289127/dependency-verification-report.html
	at org.gradle.api.internal.artifacts.ivyservice.ivyresolve.verification.ChecksumAndSignatureVerificationOverride.artifactsAccessed(ChecksumAndSignatureVerificationOverride.java:182)
	at org.gradle.api.internal.artifacts.ivyservice.ivyresolve.verification.ChecksumAndSignatureVerificationOverride$2.getFile(ChecksumAndSignatureVerificationOverride.java:200)
	at org.jetbrains.plugins.gradle.tooling.util.resolve.DependencyResolverImpl.resolveDependencies(DependencyResolverImpl.java:309)
	at org.jetbrains.plugins.gradle.tooling.util.resolve.DependencyResolverImpl.resolveDependencies(DependencyResolverImpl.java:120)
	at org.jetbrains.kotlin.gradle.KotlinMPPGradleModelBuilder.buildDependencies(KotlinMPPGradleModelBuilder.kt:229)
	at org.jetbrains.kotlin.gradle.KotlinMPPGradleModelBuilder.buildSourceSetDependencies(KotlinMPPGradleModelBuilder.kt:650)
	at org.jetbrains.kotlin.gradle.KotlinMPPGradleModelBuilder.access$buildSourceSetDependencies(KotlinMPPGradleModelBuilder.kt:39)
	at org.jetbrains.kotlin.gradle.KotlinMPPGradleModelBuilder$buildSourceSet$sourceSetDependenciesBuilder$1.invoke(KotlinMPPGradleModelBuilder.kt:173)
	at org.jetbrains.kotlin.gradle.KotlinMPPGradleModelBuilder$buildSourceSet$sourceSetDependenciesBuilder$1.invoke(KotlinMPPGradleModelBuilder.kt:39)
	at org.jetbrains.kotlin.gradle.KotlinSourceSetProto.buildKotlinSourceSetImpl(KotlinMPPGradleModelImpl.kt:27)
	at org.jetbrains.kotlin.gradle.KotlinMPPGradleModelBuilder.buildSourceSets(KotlinMPPGradleModelBuilder.kt:128)
	at org.jetbrains.kotlin.gradle.KotlinMPPGradleModelBuilder.buildAll(KotlinMPPGradleModelBuilder.kt:57)
	at org.jetbrains.plugins.gradle.tooling.internal.ExtraModelBuilder.buildAll(ExtraModelBuilder.java:115)
	at org.jetbrains.plugins.gradle.tooling.internal.ExtraModelBuilder.buildAll(ExtraModelBuilder.java:80)
	at org.gradle.tooling.provider.model.internal.DefaultToolingModelBuilderRegistry$BuilderWithParameter.build(DefaultToolingModelBuilderRegistry.java:287)
	at org.gradle.tooling.provider.model.internal.DefaultToolingModelBuilderRegistry$UserCodeAssigningBuilder.lambda$build$0(DefaultToolingModelBuilderRegistry.java:374)
	at org.gradle.configuration.internal.DefaultUserCodeApplicationContext$CurrentApplication.reapply(DefaultUserCodeApplicationContext.java:109)
	at org.gradle.tooling.provider.model.internal.DefaultToolingModelBuilderRegistry$UserCodeAssigningBuilder.build(DefaultToolingModelBuilderRegistry.java:374)
	at org.gradle.tooling.provider.model.internal.DefaultToolingModelBuilderRegistry$LockSingleProjectBuilder.lambda$build$0(DefaultToolingModelBuilderRegistry.java:304)
	at org.gradle.api.internal.project.DefaultProjectStateRegistry$ProjectStateImpl.lambda$withProjectLock$2(DefaultProjectStateRegistry.java:398)
	at org.gradle.internal.work.DefaultWorkerLeaseService.withLocks(DefaultWorkerLeaseService.java:270)
	at org.gradle.api.internal.project.DefaultProjectStateRegistry$ProjectStateImpl.withProjectLock(DefaultProjectStateRegistry.java:398)
	at org.gradle.api.internal.project.DefaultProjectStateRegistry$ProjectStateImpl.fromMutableState(DefaultProjectStateRegistry.java:379)
	at org.gradle.tooling.provider.model.internal.DefaultToolingModelBuilderRegistry$LockSingleProjectBuilder.build(DefaultToolingModelBuilderRegistry.java:304)
	at org.gradle.tooling.provider.model.internal.DefaultToolingModelBuilderRegistry$BuildOperationWrappingBuilder$1.call(DefaultToolingModelBuilderRegistry.java:337)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:204)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:199)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$2.execute(DefaultBuildOperationRunner.java:66)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$2.execute(DefaultBuildOperationRunner.java:59)
	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:157)
	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:59)
	at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:53)
	at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:73)
	at org.gradle.tooling.provider.model.internal.DefaultToolingModelBuilderRegistry$BuildOperationWrappingBuilder.build(DefaultToolingModelBuilderRegistry.java:334)
	at org.gradle.internal.build.DefaultBuildToolingModelController$AbstractToolingScope.getModel(DefaultBuildToolingModelController.java:82)
	at org.gradle.tooling.internal.provider.runner.DefaultBuildController.getModel(DefaultBuildController.java:106)
	at org.gradle.tooling.internal.consumer.connection.ParameterAwareBuildControllerAdapter.getModel(ParameterAwareBuildControllerAdapter.java:39)
	at org.gradle.tooling.internal.consumer.connection.UnparameterizedBuildController.getModel(UnparameterizedBuildController.java:113)
	at org.gradle.tooling.internal.consumer.connection.NestedActionAwareBuildControllerAdapter.getModel(NestedActionAwareBuildControllerAdapter.java:31)
	at org.gradle.tooling.internal.consumer.connection.UnparameterizedBuildController.findModel(UnparameterizedBuildController.java:97)
	at org.gradle.tooling.internal.consumer.connection.NestedActionAwareBuildControllerAdapter.findModel(NestedActionAwareBuildControllerAdapter.java:31)
	at org.gradle.tooling.internal.consumer.connection.UnparameterizedBuildController.findModel(UnparameterizedBuildController.java:81)
	at org.gradle.tooling.internal.consumer.connection.NestedActionAwareBuildControllerAdapter.findModel(NestedActionAwareBuildControllerAdapter.java:31)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction$MyBuildController.findModel(ProjectImportAction.java:581)
	at org.jetbrains.plugins.gradle.model.ClassSetProjectImportModelProvider.populateProjectModels(ClassSetProjectImportModelProvider.java:31)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction.getProjectModels(ProjectImportAction.java:290)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction.access$600(ProjectImportAction.java:42)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction$5.execute(ProjectImportAction.java:206)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction$5.execute(ProjectImportAction.java:203)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction.fetchProjectBuildModels(ProjectImportAction.java:219)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction.execute(ProjectImportAction.java:126)
	at org.jetbrains.plugins.gradle.model.ProjectImportAction.execute(ProjectImportAction.java:42)
	at org.gradle.tooling.internal.consumer.connection.InternalBuildActionAdapter.execute(InternalBuildActionAdapter.java:64)
	at org.gradle.tooling.internal.provider.runner.AbstractClientProvidedBuildActionRunner$ActionAdapter.runAction(AbstractClientProvidedBuildActionRunner.java:131)
	at org.gradle.tooling.internal.provider.runner.AbstractClientProvidedBuildActionRunner$ActionAdapter.fromBuildModel(AbstractClientProvidedBuildActionRunner.java:104)
	at org.gradle.tooling.internal.provider.runner.AbstractClientProvidedBuildActionRunner$ActionAdapter.fromBuildModel(AbstractClientProvidedBuildActionRunner.java:84)
	at org.gradle.internal.buildtree.DefaultBuildTreeModelCreator.fromBuildModel(DefaultBuildTreeModelCreator.java:57)
	at org.gradle.internal.buildtree.DefaultBuildTreeLifecycleController.lambda$fromBuildModel$1(DefaultBuildTreeLifecycleController.java:82)
	at org.gradle.internal.buildtree.DefaultBuildTreeLifecycleController.lambda$runBuild$4(DefaultBuildTreeLifecycleController.java:106)
	at org.gradle.internal.model.StateTransitionController.lambda$transition$6(StateTransitionController.java:166)
	at org.gradle.internal.model.StateTransitionController.doTransition(StateTransitionController.java:238)
	at org.gradle.internal.model.StateTransitionController.lambda$transition$7(StateTransitionController.java:166)
	at org.gradle.internal.work.DefaultSynchronizer.withLock(DefaultSynchronizer.java:44)
	at org.gradle.internal.model.StateTransitionController.transition(StateTransitionController.java:166)
	at org.gradle.internal.buildtree.DefaultBuildTreeLifecycleController.runBuild(DefaultBuildTreeLifecycleController.java:103)
	at org.gradle.internal.buildtree.DefaultBuildTreeLifecycleController.fromBuildModel(DefaultBuildTreeLifecycleController.java:74)
	at org.gradle.tooling.internal.provider.runner.AbstractClientProvidedBuildActionRunner.runClientAction(AbstractClientProvidedBuildActionRunner.java:43)
	at org.gradle.tooling.internal.provider.runner.ClientProvidedPhasedActionRunner.run(ClientProvidedPhasedActionRunner.java:53)
	at org.gradle.launcher.exec.ChainingBuildActionRunner.run(ChainingBuildActionRunner.java:35)
	at org.gradle.internal.buildtree.ProblemReportingBuildActionRunner.run(ProblemReportingBuildActionRunner.java:49)
	at org.gradle.launcher.exec.BuildOutcomeReportingBuildActionRunner.run(BuildOutcomeReportingBuildActionRunner.java:69)
	at org.gradle.tooling.internal.provider.FileSystemWatchingBuildActionRunner.run(FileSystemWatchingBuildActionRunner.java:114)
	at org.gradle.launcher.exec.BuildCompletionNotifyingBuildActionRunner.run(BuildCompletionNotifyingBuildActionRunner.java:41)
	at org.gradle.launcher.exec.RootBuildLifecycleBuildActionExecutor.lambda$execute$0(RootBuildLifecycleBuildActionExecutor.java:40)
	at org.gradle.composite.internal.DefaultRootBuildState.run(DefaultRootBuildState.java:128)
	at org.gradle.launcher.exec.RootBuildLifecycleBuildActionExecutor.execute(RootBuildLifecycleBuildActionExecutor.java:40)
	at org.gradle.internal.buildtree.DefaultBuildTreeContext.execute(DefaultBuildTreeContext.java:40)
	at org.gradle.launcher.exec.BuildTreeLifecycleBuildActionExecutor.lambda$execute$0(BuildTreeLifecycleBuildActionExecutor.java:65)
	at org.gradle.internal.buildtree.BuildTreeState.run(BuildTreeState.java:53)
	at org.gradle.launcher.exec.BuildTreeLifecycleBuildActionExecutor.execute(BuildTreeLifecycleBuildActionExecutor.java:65)
	at org.gradle.launcher.exec.RunAsBuildOperationBuildActionExecutor$3.call(RunAsBuildOperationBuildActionExecutor.java:61)
	at org.gradle.launcher.exec.RunAsBuildOperationBuildActionExecutor$3.call(RunAsBuildOperationBuildActionExecutor.java:57)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:204)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:199)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$2.execute(DefaultBuildOperationRunner.java:66)
	at org.gradle.internal.operations.DefaultBuildOperationRunner$2.execute(DefaultBuildOperationRunner.java:59)
	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:157)
	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:59)
	at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:53)
	at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:73)
	at org.gradle.launcher.exec.RunAsBuildOperationBuildActionExecutor.execute(RunAsBuildOperationBuildActionExecutor.java:57)
	at org.gradle.launcher.exec.RunAsWorkerThreadBuildActionExecutor.lambda$execute$0(RunAsWorkerThreadBuildActionExecutor.java:36)
	at org.gradle.internal.work.DefaultWorkerLeaseService.withLocks(DefaultWorkerLeaseService.java:270)
	at org.gradle.internal.work.DefaultWorkerLeaseService.runAsWorkerThread(DefaultWorkerLeaseService.java:119)
	at org.gradle.launcher.exec.RunAsWorkerThreadBuildActionExecutor.execute(RunAsWorkerThreadBuildActionExecutor.java:36)
	at org.gradle.tooling.internal.provider.ContinuousBuildActionExecutor.execute(ContinuousBuildActionExecutor.java:103)
	at org.gradle.tooling.internal.provider.SubscribableBuildActionExecutor.execute(SubscribableBuildActionExecutor.java:64)
	at org.gradle.internal.session.DefaultBuildSessionContext.execute(DefaultBuildSessionContext.java:46)
	at org.gradle.tooling.internal.provider.BuildSessionLifecycleBuildActionExecuter$ActionImpl.apply(BuildSessionLifecycleBuildActionExecuter.java:100)
	at org.gradle.tooling.internal.provider.BuildSessionLifecycleBuildActionExecuter$ActionImpl.apply(BuildSessionLifecycleBuildActionExecuter.java:88)
	at org.gradle.internal.session.BuildSessionState.run(BuildSessionState.java:69)
	at org.gradle.tooling.internal.provider.BuildSessionLifecycleBuildActionExecuter.execute(BuildSessionLifecycleBuildActionExecuter.java:62)
	at org.gradle.tooling.internal.provider.BuildSessionLifecycleBuildActionExecuter.execute(BuildSessionLifecycleBuildActionExecuter.java:41)
	at org.gradle.tooling.internal.provider.StartParamsValidatingActionExecuter.execute(StartParamsValidatingActionExecuter.java:63)
	at org.gradle.tooling.internal.provider.StartParamsValidatingActionExecuter.execute(StartParamsValidatingActionExecuter.java:31)
	at org.gradle.tooling.internal.provider.SessionFailureReportingActionExecuter.execute(SessionFailureReportingActionExecuter.java:58)
	at org.gradle.tooling.internal.provider.SessionFailureReportingActionExecuter.execute(SessionFailureReportingActionExecuter.java:42)
	at org.gradle.tooling.internal.provider.SetupLoggingActionExecuter.execute(SetupLoggingActionExecuter.java:47)
	at org.gradle.tooling.internal.provider.SetupLoggingActionExecuter.execute(SetupLoggingActionExecuter.java:31)
	at org.gradle.launcher.daemon.server.exec.ExecuteBuild.doBuild(ExecuteBuild.java:65)
	at org.gradle.launcher.daemon.server.exec.BuildCommandOnly.execute(BuildCommandOnly.java:37)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.WatchForDisconnection.execute(WatchForDisconnection.java:39)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.ResetDeprecationLogger.execute(ResetDeprecationLogger.java:29)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.RequestStopIfSingleUsedDaemon.execute(RequestStopIfSingleUsedDaemon.java:35)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.ForwardClientInput$2.create(ForwardClientInput.java:78)
	at org.gradle.launcher.daemon.server.exec.ForwardClientInput$2.create(ForwardClientInput.java:75)
	at org.gradle.util.internal.Swapper.swap(Swapper.java:38)
	at org.gradle.launcher.daemon.server.exec.ForwardClientInput.execute(ForwardClientInput.java:75)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.LogAndCheckHealth.execute(LogAndCheckHealth.java:55)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.LogToClient.doBuild(LogToClient.java:63)
	at org.gradle.launcher.daemon.server.exec.BuildCommandOnly.execute(BuildCommandOnly.java:37)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.EstablishBuildEnvironment.doBuild(EstablishBuildEnvironment.java:84)
	at org.gradle.launcher.daemon.server.exec.BuildCommandOnly.execute(BuildCommandOnly.java:37)
	at org.gradle.launcher.daemon.server.api.DaemonCommandExecution.proceed(DaemonCommandExecution.java:104)
	at org.gradle.launcher.daemon.server.exec.StartBuildOrRespondWithBusy$1.run(StartBuildOrRespondWithBusy.java:52)
	at org.gradle.launcher.daemon.server.DaemonStateCoordinator$1.run(DaemonStateCoordinator.java:297)
	at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:64)
	at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:48)
	at java.base@11.0.11/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
	at java.base@11.0.11/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
	at java.base@11.0.11/java.lang.Thread.run(Thread.java:829)

BUILD SUCCESSFUL in 538ms

```

## Various observations

1. Opening root `build.gradle` and uncommenting line #14 `// mavenCentral()` will make sync work.
2. Deleting `gradle/verification-metadata.xml` will make sync work.
3. This project is using file repository
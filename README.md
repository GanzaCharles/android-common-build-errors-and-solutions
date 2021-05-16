--------------------
Module not specified
--------------------
* delete **project.iml** file

------------------
App not installed
------------------
* delete **{module name}\app\build\outputs\apk**
Kapterror -> Run with gradle assembleMyBuild --stacktrace or --debug. If it fails, run code inspection. 
* use **adb install app.apk** command to get the error message.


----------------------------------
Nested/fragment crashing after applying theme or configuration change. 
----------------------------------
* Quick solution: use findById or instatiate fragment using xml (fragment tag).
* Solution: check if onViewCreated superclass is being invoked and that the fragment is properly destroyed.

-------------------
App flavor variant not installing.
-------------------
* **clean build** and build project again.

-------------------------------------------------------------
Dagger Hilt — ViewModelClass has no zero argument constructor
-------------------------------------------------------------
* make sure you annotated your Fragment/Activity **@AndroidEntrypoint**
* make sure you annotated your ViewModel with **@HiltViewModel** and its constructor with **@Inject**

-------------------------------------------------------------------------------------
A failure occurred while executing org.jetbrains.kotlin.gradle.internal.KaptExecution
-------------------------------------------------------------------------------------
* run with gradle build --scan
* add **kapt.verbose=true** in **gradle.properties** file
* make sure your fields aren't private if injecting them with **Hilt**

--------------------------------------
Cannot resolve InstantTaskExecutorRule
--------------------------------------
* add the following in your module-level gradle.build file

```
androidTestImplementation "androidx.arch.core:core-testing:2.1.0"
implementation "androidx.arch.core:core-testing:2.1.0"
```

----------------------------------
Cannot inline bytecode built with JVM target 1.8 into bytecode that is being built with JVM target 1.6
----------------------------------
* Solution: in module level **build.gradle**, add:
  
```
compileOptions {
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
}
kotlinOptions {
    jvmTarget = JavaVersion.VERSION_1_8
}
```

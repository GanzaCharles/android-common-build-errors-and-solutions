Problem: Module not specified
Solution: delete project.iml file
----------------------------------
Problem: App not installed: delete {project name}\app\build\outputs\apk
Kapterror -> Run with gradle assembleMyBuild --stacktrace or --debug. If it fails, run code inspection. 
------------------------
Problem: Nested/fragment crashing after applying theme or configuration change. 
Quick solution: use findById or instatiate fragment using xml (fragment tag).
Solution: check if onViewCreated superclass is being invoked and that the fragment is properly destroyed.
-----------------
App not installing, use "adb install app.apk" command to get the error message.
-------------------
Problem: App flavor variant not installing.
Solution: clean build and build project again.
-----------------
Problem: Cannot inline bytecode built with JVM target 1.8 into bytecode that is being built with JVM target 1.6
Solution: in module level build.gradle, add:
     
compileOptions {
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
}
kotlinOptions {
    jvmTarget = JavaVersion.VERSION_1_8
}

### AR Core Sample for Xamarin Android

Originally fetched from https://github.com/xamarin/XamarinComponents/tree/master/Android/ARCore (based on the blog post at https://blog.xamarin.com/augmented-reality-xamarin-android-arcore). 

It didn't work out of the box any more. It had references to Android bindings projects for ARCore (`arcore.aar`) and Java.OpenGL (`obj.jar`) files in a 'externals' directory, which didn't exist.

Had to pull down the entire repo and then run the build script (referenced by the `README.md` at the above linked location), which failed (it couldn't find the `libs` target). However it ran for long enough that it was able to pull down the `arcore.aar` and `obj.java` files into a newly created `externals` directory before it died.

Turns out we didn't actually need the `arcore.aar` bindings project, since the ARCore library now exists as a nuget (which has been added to this project as a reference to '1.0.0'). This version of the nuget doesn't support vertical surfaces yet, tho I hope that'll be done soon.

I've actually embedded the `obj.jar` file into this repo, and moved the `externals` directory into this solution's folder structure. You should now be able to pull this down and build it straight away.

**A note when running the app**: The first time you launch it, it requests permission to use the camera. But there's a race condition that pops up a message saying your device doesn't support ARCore (and it throws an exception in the debugger). Just accept the camera permission request and relaunch the app, and it should work (unless your device really doesn't support ARCore :)).

There's more stuff, quick-starts, etc. at https://developers.google.com/ar/develop/ (including a list of supported OS's and phones). There's a reasonable amount of heavy lifting for you to do if you want to get it running with Unreal or Unity or some of the other things.


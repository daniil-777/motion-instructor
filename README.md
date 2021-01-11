# MR Motion Instructor
[**Report**](https://placeholder) | [**Presentation**](https://placeholder) | [**Video**](https://placeholder)

[Jan Wiegner](https://github.com/janwww), [Rudolf Varga](https://github.com/ketjatekos), [Felix Pfreundtner](https://github.com/felixpfreundtner), [Daniil Emtsev](https://github.com/daniil-777) and [Utkarsh Bajpai](https://github.com/Utkarsh-Bajpai)

# Abstract
Learning complex movements can be a time-consuming process, but it is necessary for the mastery of activities like Karate Kata, Yoga and dance choreographies. It is important to have a teacher in person to demonstrate the correct pose sequences step by step and correct errors in the student’s body postures.
In-person sessions can be impractical due to epidemics or travel distance, while videos make it hard to see the 3D postures of the teacher and of the students. As an alternative, we propose the teaching of poses in Augmented Reality (AR) with a virtual teacher and 3D avatars.

## Open source usage
TODO update this:

This work is based on [this repository](https://github.com/curiosity-inc/azure-kinect-dk-unity) (MIT License), which is an example C# wrapper showing how to use Azure Kinect DK in Unity. In particular, we used code from [this fork](https://github.com/Aviscii/azure-kinect-dk-unity). We upgraded the Azure Kinect Body Tracking SDK and Azure Kinect SDK.
As alternative to pose estimation with Kinect we used [Lightweight human pose estimation](https://github.com/Daniil-Osokin/lightweight-human-pose-estimation-3d-demo.pytorch) (Apache-2.0 License). 

## Environment
As of December 10, 2020, this repository has been tested under the following environment:
- Windows 10 Education (10.0.19042 Build 19042)
- [all tools required to develop on the Hololens](https://docs.microsoft.com/en-us/windows/mixed-reality/install-the-tools)
- Unity 2019.4.13f1 // Unity 2019 LTS version
- GTX 1070

## Get Started
1. Clone this repository.
2. Setup the Azure Kinect Libraries: (same as [Sample Unity Body Tracking Application](https://github.com/microsoft/Azure-Kinect-Samples/tree/master/body-tracking-samples/sample_unity_bodytracking))
    1. Get the latest nuget packages of libraries:
        - Open the Visual Studio Solution (.sln) associated with this project. You can make one by opening a csharp file the Unity Editor.
        - In Visual Studio open: Tools->NuGet Package Manager-> Package Manager Console
        - Exectue in the console: `Install-Package Microsoft.Azure.Kinect.BodyTracking -Version 1.0.1`
    2. Move libraries to correct folders:
        - Execute the file `unity/MoveLibraryFile.bat`. You should now have library files in `unity/` and in the newly created `unity/Assets/Plugins`.
3. Open the `unity` folder as a Unity project, with `Universal Windows Platform` as the build platform. It might take a while to fetch all packages.
4. Open `Assets/PoseteacherScene`.
5. When prompted to import TextMesh Pro, select `Import TMP Essential Resources`. You will need to reopen the scene to fix visual glitches.
6. Connect to the Hololens with [Holographic Remoting](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Tools/HolographicRemoting.html#connecting-to-the-hololens-with-wi-fi) (using the `Windows XR Plugin Remoting` in Unity).
7. Click play inside the Unity editor.

### Notes
- Most of the application logic is inside of the `PoseteacherMain.cs` script which is attached to the `Main` game object.
- If updating from an old version of the project, be sure to delete the `Library` folder generated by Unity, so that packages are handled correctly. 
- The project uses MRTK 2.5.1 from the Unity Package Manager, not imported into the `Assets` folder: 
   - MRTK assets have to be searched in inside `Packages` in the editor.
   - The only MRTK files in `Assets` should be in folders `MixedRealityToolkit.Generated` and `MRTK/Shaders`. 
   - Only exception is the `Samples/Mixed Reality Toolkit Examples` if [MRTK examples are imported](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#using-mixed-reality-toolkit-examples)
   - If there are other MRTK folders, they are from an old version of the project (or were imported manually) and [should be removed like when updating](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Updating.html). 
     Remeber to delete the `Library` folder after doing this.
- We use the newer XR SDK pipeline instead of the Legacy XR pipeline (which is depreciated)

## How to use
- It is recommended to use the UI to navigate in the application.
- For debugging we added the following keyboard shortcuts: (some currently unavailable)
   - H for toggling Hand menu in traing/choreography (for use in editor testing)
   - ~~X for normal operation~~
   - ~~Y for recording~~
   - ~~Z for playback~~
   - ~~L to load playback~~
   - ~~R to reset/delete saved playback~~

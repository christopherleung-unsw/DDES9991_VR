# Unreal Engine VR
This MSIT Capstone project explores the VR capabilities of <b>Unreal Engine 5.4.4</b>.<br>
An ArchVis demo was used as a base to showcase and compare UE’s features, found under ```Content/_DDES9991_Showcase```, with a video showcase viewable [here](https://youtu.be/APmUC50VlbE).<br>
<br>
A more detailed and general guide covering UE's features can be found [here](_Guides/UE_VRGuide_CL.pdf). Else, to quickly get started the mandatory steps can be found below.<br>
## Getting Started
In order to preview anything in VR, make sure that your OpenXR Runtime software (e.g. Quest Link) is running <b><i>before</i></b> you launch your project. Not doing so might prevent you from accessing the ‘VR Preview’ Play mode.<br>
<br>
<img width="433" height="252" alt="PlayVRPreview" src="https://github.com/user-attachments/assets/567e111a-0379-4528-a037-ebb496717adf" />
<br>
<br>
Check the <b><i>Scalability</i></b> settings before previewing the project. The ```Medium``` preset with <b>Global Illumination</b> and <b>Reflections</b> on ```High``` is a good starting point when using Lumen, adjust according to your hardware <i>(Lumen does <b>NOT</b> work on ```Low``` or ```Medium``` Scalability)</i>.<br>
Without Lumen setting everything to ```High``` might give you a similar performance (depending on your hardware).<br>
<br>
<img width="398" height="320" alt="Scalability" src="https://github.com/user-attachments/assets/54187254-d982-4dc0-8074-e1fec04d6405" />
<br>
## Plugins
For the best experience, it is recommended to download some plugins.<br>
### Nvidia DLSS
Nvidia DLSS is a third party plugin providing access to Multi Frame Generation, Frame Generation, Ray Reconstruction, Super Resolution, DLAA, Reflex Low Latency, and NVIDIA Image Scaling. It was an essential part in getting a smooth enough frame rate in VR with the available hardware. However, it is restricted to Nvidia GPUs and Temporal AA. It can be downloaded [here](https://developer.nvidia.com/rtx/dlss).<br>
<br>
The required components for this project are:<br>
- DLSS
- NIS
- Streamline
- StreamlineCore
- StreamlineDeepDVC
- StreamlineDLSSG
- StreamlineNGXCommon
- StreamlineReflex

You can install them by copying each folder to your Unreal Engine Plugins directory. Usually found under ```C:\Program Files\Epic Games\UE_5.4\Engine\Plugins\Marketplace```, and activate them using UE's Plugin window.<br>
<br>
### Console Variables Editor
The Console Variables Editor can be enabled straight from the UE’s Plugin window. It allows for a list of CVars to be saved as presets and be run at any time for debugging and testing.<br>
<br>
<img width="573" height="226" alt="ConsoleVariablesEditor" src="https://github.com/user-attachments/assets/e1b65b19-fe1e-4bce-bf98-ec6f03543100" /><br>
<br>
### Meta Asynchronous Spacewarp
If you're using a Meta Quest headset, Quest Link has a software limit called ```Asynchronous Spacewarp``` that <b>halves the FPS</b> of your headset if the projected experience cannot reach the targeted FPS, and uses interpolation to reach the desired target.<br>
<br>
<img width="502" height="340" alt="ASW" src="https://github.com/user-attachments/assets/6cf3d299-5a15-4299-bd18-7aa2d0e10a62" /><br>
<br>
However, I found some artefacts around the edges of the frame when it was being activated in UE and decided to fully disable it through the Oculus Debugging Tool (usually found at ```C:\Program Files\Oculus\Support\oculus-diagnostics\OculusDebugTool```)<br>
<br>
Note that this setting resets to <b>Auto</b> every time the Quest Link app is restarted. It can be modified permanently through Regedit:<br>
1. Go to ```HKEY_LOCAL_MACHINE\SOFTWARE\Oculus```
2. Add a new ```DWORD``` called ```AswDisabled``` and set to ```1```
3. Restart OVRServer
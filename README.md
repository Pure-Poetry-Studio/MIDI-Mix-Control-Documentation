## Introduction

### 1.1 Purpose

MIDI Mix Control is an Unreal Engine 5 plugin that leverages the [Editor Utility Widget](https://dev.epicgames.com/documentation/en-us/unreal-engine/editor-utility-widgets-in-unreal-engine?application_version=5.3) system. It allows a user to control their audio modulation mixes with their MIDI controllers while also providing a user-friendly interface that provides real-time feedback.

## System Overview

### 2.1 Architecture

MIDI Mix Control serves the user by easily creating a bridge between Unreal Engine's [MIDI Device Support](https://dev.epicgames.com/documentation/en-us/unreal-engine/midi-in-unreal-engine?application_version=5.3) and a user's MIDI control devices. It currently only supports Unreal Engine's [Audio Modulation](https://dev.epicgames.com/documentation/en-us/unreal-engine/audio-modulation-in-unreal-engine?application_version=5.3) system as a means to control the overall volume of different elements in a project's soundscape. 

### 2.2 Dependencies

Required plugins: MIDI Mix Control depends on Unreal Engine's official Audio Modulation, MIDI Device, Editor Scripting Utilities, and Sound Utilities plugins. As these dependencies are already embedded into the plugin descriptor, they are installed and enabled automatically during the installation of MIDI Mix Control. 

MIDI Control Surfaces: While MIDI Mix Control is made to work with external MIDI controllers, it has a user-friendly interface to control and observe real-time changes in Control Bus Mix profiles the user selects. For this reason, theoretically it is possible to use this plugin without any MIDI controllers as well, but this approach is not recommended as there might be unpredictable bugs and behaviors occurring. 

## Installation Guide

### 3.1 Prerequisites

Unreal Engine versions: 5.3.2 or 5.4.2 (please make sure to download the correct version of the plugin to install into your engine)

### 3.2 Installation Steps

#### 3.2.1 Itch.io

1. Unzip the plugin file you downloaded to a place of your choosing. 
2. Go to the relevant engine plugin folder, depending on your engine version this will be `[Your Install Directory]\Epic Games\[Engine Version]\Engine\Plugins`

 - For example, if my Unreal Engine version 5.3 is installed on my D drive, under Program Files, the correct directory would be `D:\Program Files\Epic Games\UE_5.3\Engine\Plugins`

Once you are inside the Plugins folder, if you already have a Marketplace folder, navigate into that, and if you don't have one, please create one and open it. 
 
 - Current directory would be `D:\Program Files\Epic Games\UE_5.3\Engine\Plugins\Marketplace`

Now please copy and paste the unzipped plugin folder inside the Marketplace directory. Make sure the unzipped plugin has the structure of MIDIMixControl\[All Plugin Contents] and not another structure due to unzipping to a specific directory.

 - Now the final directory structure should be `D:\Program Files\Epic Games\UE_5.3\Engine\Plugins\Marketplace\MIDIMixControl`

As MIDI Mix Control is made and structured as an engine plugin, now you can easily enable/disable it for your projects by using the Plugins window under Edit/Plugins from the toolbar. 

![image](https://github.com/Pure-Poetry-Studio/Midi-Mix-Control/assets/6593585/a9eb50cd-2a34-4902-be39-b4476e443b71)

 _make sure to restart the editor after you enable the plugin_

![image](https://github.com/Pure-Poetry-Studio/Midi-Mix-Control/assets/6593585/1e35201b-25f4-49cc-8d9a-68b16d3c3e25)



#### 3.2.2 Epic Marketplace 
After download, just press the "Install to Engine" button and choose the right version matching your installed Unreal Engine 5 version. The plugin will be installed, and you can easily enable/disable it from the Plugins window under Edit/Plugins from the toolbar.


## Usage Guide

 - **_If you would like a sample project you can test the plugin on to experience the steps outlined below, please [download the correct version of MIDI Mix Playground sample project here](https://drive.google.com/drive/folders/1XPoJcuZaC_ce81pPnAVX-dO0jBvkcc34) and open it in Unreal Engine._**

### 4.1 User Interface Overview

![image](https://github.com/Pure-Poetry-Studio/Midi-Mix-Control/assets/6593585/27944325-98ac-4273-8fb8-70b8dc21bec5)


MIDI Mix Control has three main sections, 

- On top left, you can find dedicated buttons to save/reset plugin settings, deactivating solo/all mixes, selecting different mixes to control, or change your midi controller and/or it's knob/fader assignment as necessary.
- On top middle, you can see a grid of Control Bus Mix profiles, you can easily save/load profiles up to 10 (11, including the default profile) to test different gameplay/audio scenarios with click of a button. 
- On bottom, you will see a dedicated row of channel strips, these channels are automatically populated from the selected Control Bus Mix during first load (if you have saved plugin data) or when a Control Bus Mix is selected from the dropdown. These channel strips react in real-time to the movements of your midi controller fader/knobs and can also be controlled via mouse pointer.


### 4.2 Core Functionality

#### 4.2.1 Save / Load Plugin Settings and Mix Profiles

On first load, you will get a Nothing To Load notification as you won't have any saved plugin data. 

It is vital to Save Plugin Settings before you close the Unreal Engine 5 editor. As long as the editor session is open, even if you close the plugin window and re-open it your data will be saved locally. However, unless you choose to save your plugin settings like the selected control bus mix, and MIDI controller fader assignments, before a full editor close, when you re-open the project you will have to select a Control Bus Mix again and re-assign your faders.

**Save Plugin Settings** and **Reset Plugin Settings** buttons are only enabled when the editor is not in Play mode,however you can still save your mix profile changes during playtime, by clicking the save button corresponding to the profile number of your choosing, when you reach a satisfactory mix. Please keep in mind, unless you save your mix profile changes during playtime, they will be lost when you stop the editor, so save your mix profiles before you press the stop button.

#### 4.2.2 MIDI Controller Support

When you first load a Control Bus Mix, the auto-assign mode for the faders/knobs on your controller will be on, at this point the first fader or knob you touch will be assigned to the first channel strip visible on the bottom section, and all faders/knobs will automatically be assigned sequentially. 

![image](https://github.com/Pure-Poetry-Studio/Midi-Mix-Control/assets/6593585/b29d872b-a5d9-41cd-8b6b-ba74414ddb06)

e.g. if you select the Test Control Bus Mix from the dropdown, and then touch the first fader on your controller, it will be assigned to the Ambience Control Bus, the second will be assigned to the SFX Control Bus and so on. And consequentially, if you touch the third knob/fader on your controller it will be registered as the first channel controller. In case of mistaken assignment, you can simply click the Re-Assign button and start over.

**IMPORTANT**

While controller and fader assignments are preserved between editor sessions, thanks to the Save Plugin Settings option, it is important to be aware that when you select another controller, auto-assign mode will be on automatically, and you need to re-assign your fader/knobs again. e.g. if I switch from MPK to Novation on the dropdown...

![image](https://github.com/Pure-Poetry-Studio/Midi-Mix-Control/assets/6593585/3c986284-25e6-4331-afa6-deb5bd63ff2f)


...I need to touch the first fader I would like to assign to the first channel strip again. But as long as I save this new assignments by using the Save Plugin Settings button, it will be recalled when I re-open the Editor Utility Widget or the editor again. 


### 4.3 Troubleshooting

 **I get "Nothing To Load" notification on first load/subsequent loads.**

 Please verify that your Control Bus Mix has a mix saved on mix Profile Index 0. When you first create a Control Bus Mix, it might not auto save the asset, or save the Mix to a profile, so it is necessary that you save it to Profile Index 0 to recall it on MIDI Mix Control's first load of the selected Control Bus Mix, as it automatically calls Profile Index 0 when there isn't a saved plugin data for preferred current Profile Index. 

![image](https://github.com/Pure-Poetry-Studio/Midi-Mix-Control/assets/6593585/8d3a4c84-a3ba-489c-a1f2-08d04391fc63)

Afterward, you can easily save different variations of your mix to other profile indexes by using the MIDI Mix Control interface itself.


## Support and Maintenance

### 5.1 Frequently Asked Questions (FAQs)

   **Can I use this to connect/auto-assign my MIDI controllers to Submixes/Metasounds etc.?**
     
At this time, as a solo developer, I am only able to support the development/maintenance of MIDI Mix Control for Audio Modulation mixes. I have many features planned for this plugin (you can check some of them on the roadmap below) for the foreseeable future, including supporting MIDI Controller to Submix control support, however it will largely depend on how much time I can justify spending on it from a financial standpoint. So, if you would like to see this plugin developed further, please buy, gift, spread the word, or you can support me directly via PayPal.

### 5.2 Contact Information

For all questions, requests, feedbacks, please get in touch via contact at purepoetry dot studio

### 5.3 Feature Roadmap

Some of the features I am planning to develop and release to begin with in the near future,

- Support other Audio Modulation values other than Volume
- Add support for Submixes
- Add support for using different MIDI Channels on the same device for better UX
- Keep Fader/Knob assignment information per MIDI Controller and recall when MIDI Controller is selected again, instead of triggering Auto-Assign

As long as it is being used/paid for, this plugin will be kept up-to-date with all current Unreal Engine 5 versions, and provide support and add new features.

## Change Log

### 6.1 Version History

1.0.0 - June 7th, 2024

IT IS SHIPPED!


Copyright Berrak Nil Boya, All Rights Reserved.

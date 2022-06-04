# AdeptiScanner-GI
OCR-based inventory scanner for Genshin Impact, with both a manual and automatic mode.

### _Please read instructions below before using. Download link for the latest version can be found [here](https://github.com/D1firehail/AdeptiScanner-GI/releases)_

AdeptiScanner requires some tools produced by Microsoft to work, they're commonly used in games so you're likely to already have them.
 - If the scanner throws an error on startup, you may be missing them. [Download links for their installers can be found here](https://docs.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022). ***You need both x86 and x64***

## Warnings and important notes
- ***For the automated scanning mode of this program to work, it needs to run as admin.***
- While using the auto mode, the program will take control of your mouse. You can press escape during the scan to pause it. Do not move or use your mouse during auto unless paused.
- According to my interpretation of the [Genshin TOS](https://genshin.mihoyo.com/en/company/terms), use of this scanner should be allowed as I do not believe it causes an unfair competitive advantage. To my knowledge, nobody has gotten in trouble for the use of this or similar programs so far, but if you're worried about it I suggest avoiding the auto mode.
- AdeptiScanner relies on specific colour values and a white window header to identify the contents of the image
    - Anything that changes in-game colours can mess up the results. Examples of programs/features that can interfere is Reshade, Windows Night Light, F.lux, Nvidia Filters and Colourblind compensation tools.
    -   If your window header for the game is not white, try changing it in Windows settings (Themes -> Colours). If that isn't an option, you can try tricking it by covering the window header with a mostly white window like notepad.

## Updating for a new version
- For the vast majority of game updates, all you should need is to replace the `ArtifactInfo.json` file inside `ScannerFiles` with an updated one. You can find the latest version [here](https://raw.githubusercontent.com/D1firehail/AdeptiScanner-GI/master/AdeptiScanner%20GI/ScannerFiles/ArtifactInfo.json)
- Downloading the full scanner again should only be needed to get improvements to the scanner itself

## How to prepare for scanning
1. Set the game to run in windowed mode at a resolution of 1600x900
    - It may work for other resolutions, but it's likely to run into issues for lower resolutions or different aspect ratios
2. Place the game window in a position that covers the middle of your ***-primary-*** display.
    - ***Make sure nothing is covering the game window!***
    - Example window position for 1080p monitor. Notice that the preview portion of the window is off-screen while doing the initial capture or using auto ![Example window position for 1080p monitor](https://github.com/D1firehail/AdeptiScanner-GI/blob/master/1080p-example.png?raw=true)
3. Open the artifact section on your main backpack and select a 5 star artifact with a full length item description
        - Example ![Example](https://github.com/D1firehail/AdeptiScanner-GI/blob/master/Capture-length-example.png?raw=true)
4. Press "Capture"
    - Make sure the preview matches the good example, if it doesn't, try moving your camera around a bit in-game to change the background and repeat again from step 3 ![something like this](https://github.com/D1firehail/AdeptiScanner-GI/blob/master/Capture-example.png?raw=true)
5. (Optional) Enter your in-game name / traveler name in the `Traveler Name` text box.
    - Not entering this will cause any scanned artifacts that are equipped on your Traveler to be incorrectly detected as either equipped on the wrong character or not equipped at all

You're now ready for manual or automatic artifact scanning

### Manual scanning
1. Follow the instructions under `How to prepare for scanning`. Do not move the game window and do not cover the captured area while scanning
2. Select the artifact you wish to scan and press the `Read Stats` button
    - The scanner is mainly tested for 4 and 5 star artifacts. While it has the information about all tiers of artifacts, it may be unable to read some lower tier ones
3. Repeat step 2 for every artifact you wish to manually scan

### Automated scanning
- While using the auto mode, the program will take control of your mouse. You can press escape during the scan to pause it.
- Do not move or use your mouse during auto unless paused.
- Automated scanning will only work properly if this program is being run as admin
- Automated scanning is expected to work for 4 and 5 star artifacts, it's not expected to automatically scroll through any lower tier artifacts
1. Follow the instructions under `How to prepare for scanning`. Do not move the game window and do not cover ***ANY*** part of the game while using auto
2. Scroll your artifact list so the **stars** for the **top row** and the **white/beige label** for the **bottom row** are **both fully visible** with some margin. ![something like this](https://github.com/D1firehail/AdeptiScanner-GI/blob/master/scroll-example.png?raw=true)
3. Press the `Start Auto` button
    - During the scan, you can press the escape button on your keyboard to pause it
    - `Resume` will make the scanner resume the scan
    - `Stop after processing` will make the scanner stop scrolling through new artifacts immediately, but finish processing all scanned ones
    - `Stop now` will make the scanner immediately exit automated scanning, not saving any scanner artifacts
4. The scanner will automatically stop once it thinks it's done scrolling through the artifact list or finds an artifact with identical stats to a previous one.

### Exporting results
1. Scan artifacts using manual, automatic scanning or a combination of the two
2. Configure the `Export Filters` section according to your wishes
    - You can use a template file that everything except artifact details will be copied from. To do this, place a GOOD-format json in the `ScannerFiles` folder and rename it to `ExportTemplate.json`    
3. Press the `Export Results` button, your results will be placed in a timestamped file in the `ScannerFiles` folder
    - You can change your export filters and press the export button more than once if you so wish, each export will appear as a separate file

## How to contact
- Create an issue or pull request on this repo
- I haven't created a discord, as I have no idea how much interest there will be. If one is needed in the future I'll create one
- I'm in the community-created [Genshin Dev Discord](https://discord.gg/CnmeBYSHaC), same username as on here
- I'm also in the [Genshin Optimizer Discord](https://discord.com/invite/CXUbQXyfUs). Feel free to @ me for smaller issues, but for longer things it's better to stick to the Genshin Dev discord or DMing me

## Acknowledgements
- Some functions used are heavily based on code from [WFInfo](https://github.com/WFCD/WFinfo), an OCR-based companion program for Warframe
- The tesseract model used was trained and provided by the creator of [this similar program](https://github.com/Andrewthe13th/Genshin_Scanner)
- The main purpose of this scanner is to more easily import your artifacts into [Genshin Optimizer](https://frzyc.github.io/genshin-optimizer/), but it should be compatible with any other program that uses the GOOD format

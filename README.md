# **Audio Enhancer**

This project processes audio files by separating specific stems (e.g., vocals) and enhancing the extracted audio by removing silence, normalizing volume, and applying fade effects.

## **Features**
- Extracts specific audio stems (e.g., vocals) using **Ultimate Vocal Remover (UVR)**.
- Enhances the extracted audio by:
  - Removing silent parts.
  - Normalizing volume.
  - Applying fade-in and fade-out effects.
- Saves the enhanced audio in **WAV format**.

---

## **Project Structure**
```
Audio_Enhancer/
│── uvr/                     # UVR module for stem separation
│── audio_enhancer.py        # Main script for processing and enhancing audio
│── requirements.txt          # Dependencies required for the project
│── README.md                 # Project documentation
```

---

## **Installation**
### **1. Install Dependencies**

### **Prerequisites**  
Ensure you have **Python 3.10** (recommended) installed on your system.  

### **Setting Up the Virtual Environment**  
1. **Navigate to the Project Directory**  
   - Open a terminal or command prompt.  
   - Ensure you are inside the `Audio_Enhancer` directory. The terminal path should resemble:  
     ```shell
     C:\User\Audio_Enhancer>
     ```  

2. **Create a Virtual Environment**  
   - Run the following command to create a virtual environment:  
     ```shell
     python -m venv env
     ```  
   - This will generate a new folder named `env` inside the project directory.  

3. **Activate the Virtual Environment**  
   - Navigate to the `env` directory:  
     ```shell
     cd env
     cd Scripts
     ```  
   - Activate the virtual environment by running:  
     ```shell
     activate.bat
     ```  
   - Once activated, the terminal prompt will change to indicate that the virtual environment is active.  

4. **Deactivating the Virtual Environment**  
   - To deactivate, simply run:  
     ```shell
     deactivate
     ```  

5. **Return to the Project Directory**  
   - After activating the virtual environment, navigate back to the `Audio_Enhancer` directory:  
     ```shell
     cd ..
     cd ..
     ```  

Then, install the required dependencies:

```bash
pip install -r requirements.txt
```

> **Note:** The **Ultimate Vocal Remover (UVR)** package should be installed and configured properly.

### **2. Install FFmpeg**
The script uses `pydub`, which requires **FFmpeg**. Install it by following these steps:

- **Windows**: [Download FFmpeg](https://ffmpeg.org/download.html)

    1. **Download FFmpeg**  
    - Open a web browser.  
    - Navigate to **[Windows build from gyan.dev](https://www.gyan.dev/ffmpeg/builds/)**.  
    - Under **"Git Master Builds,"** locate and download:  
        ```text
        ffmpeg-git-full.7z
        ```
    
    2. **Extract and Move FFmpeg**  
    - Once downloaded, extract the `.7z` file using **WinRAR** or **7-Zip**.  
    - Move the extracted folder to:  
        ```text
        C:\Program Files\
        ```
    - Open the extracted folder, navigate to the **bin** directory, and copy the full path. Example:  
        ```text
        C:\Program Files\ffmpeg-7.1-full_build\bin
        ```

    3. **Set Up Environment Variables**  
    - In the **Windows Search Bar**, type:  
        ```text
        Edit the system environment variables
        ```  
    - Click on **Environment Variables** at the bottom of the window.  
    - Under **User Variables**, locate and select **Path**, then click **Edit**.  
    - In the **Edit Environment Variable** window, click **New**, paste the copied FFmpeg **bin** path, and click **OK**.  
    - Click **OK** on all open windows to save the changes.  

- **Linux/macOS**: Install it using:

  ```bash
  sudo apt install ffmpeg   # Ubuntu/Debian
  brew install ffmpeg       # macOS (Homebrew)
  ```
To check if FFmpeg is installed on your system and verify its installation, you can follow these steps in the command prompt:
1. **Open the Command Prompt**:
- On Windows: Press `Windows + R`, type `cmd`, and press Enter.
- On macOS/Linux: Open the Terminal application.
2. **Type the following command**:
```
ffmpeg -version
```
3. **Press Enter**.
### Expected results:
- If FFmpeg is installed correctly, you should see output detailing the installed version of FFmpeg, along with various configuration options and libraries.
- If FFmpeg is not installed, you will see a message like `'ffmpeg' is not recognized as an internal or external command` (on Windows) or `command not found` (on macOS/Linux).

---

## **Usage**
### **1. Basic Usage**
Modify the script with your input and output paths, then run:

```python
from audio_processor import process_audio

enhanced_file = process_audio(
    audio_file="C:/Users/input/audio.mp3", #Add the audio file path
    output_dir="C:/Users/output", #Add the output directory path
    single_stem="Vocals"
)
print(f"Enhanced file saved to: {enhanced_file}")
```

---

## **Functionality Breakdown**
### **1. `process_audio`**
- Loads the UVR model.
- Separates the requested stem (e.g., Vocals).
- Enhances the extracted audio.

### **2. `enhance_audio`**
- Removes silent parts.
- Normalizes the volume.
- Applies fade-in and fade-out effects.
- Saves the enhanced file in **WAV format**.

---

## **Parameters**
| Parameter         | Description                                                      | Default Value |
|------------------|------------------------------------------------------------------|--------------|
| `audio_file`    | Path to the input audio file.                                    | Required     |
| `output_dir`    | Directory where the output will be saved.                        | Required     |
| `single_stem`   | Specify which stem to extract (`Vocals`, `Drums`, etc.).         | `"Vocals"`   |

---

## **Output Files**
- The script saves the **enhanced** audio file as `_enhanced.wav` in the output directory.
- The separated file (before enhancement) is **automatically deleted** to keep the output folder clean.

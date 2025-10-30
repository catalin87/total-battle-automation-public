# Total Battle Automation Tool

An automated screen automation tool for Total Battle game that uses advanced image recognition to automate crypt exploration.

## Features

- ✅ Automatic telescope button detection
- ✅ Smart creature icon capture and recognition
- ✅ Multi-scale template matching for zoom-independent detection
- ✅ Window resizing for pixel-perfect automation (1080x800)
- ✅ Real-time GUI with logs and preview images
- ✅ Automatic close button cleanup on errors
- ✅ Cycling through different Go buttons for optimal creature detection
- ✅ Intelligent Explore button selection (rightmost button)
- ✅ Multi-monitor support

## Requirements

- Python 3.12 (required for numpy compatibility)
- Windows 10/11
- Total Battle game in windowed mode

## Quick Start

### Option 1: Download Pre-built Executable (Easiest for non-technical users)
1. Go to the [Releases](https://github.com/catalin87/total-battle-automation/releases) page
2. Find the latest release (e.g., v1.0.0)
3. Download `TotalBattleAutomation.exe` from the Assets section
4. Double-click to run (no Python installation needed!)

**Note:** The executable is a standalone file - just download and run!

### Option 2: Double-click to run (For developers)
Just double-click `start.bat` file to launch the application!

### Option 3: Command line
```bash
cd app
py -3.12 automation_launcher.py
```

## Installation

1. Install Python 3.12 (if not already installed)
2. Install dependencies:
```bash
py -3.12 -m pip install -r requirements.txt
```

## Setup Before Running

To run this tool, you must:

1. **Open the game in windowed mode** (NOT fullscreen)
2. **Put Carter as your 1st Captain**
3. **Click Watchtower** and select desired level and type of crypts, then close it
4. **Make sure to not have any item in the "Speed-up" area!**
5. If you have multiple monitors, put the game on the main monitor
6. Minimum resolution is 1280 width

## How It Works

The automation performs the following steps:

1. **Resizes game window** to 1080x800 for pixel precision
2. **Clicks telescope button** to open Watchtower
3. **Finds and captures creature icon** from the 3rd or 4th Go button
4. **Clicks Go button** to go to map
5. **Searches for creature on map** using multi-scale matching in center area
6. **Clicks the creature** when found
7. **Handles Open/Explore buttons** - clicks "Open" if present, then clicks rightmost "Explore" button
8. **Speed ups the march** and uses speed-up items
9. **Monitors for completion** and repeats the process

## GUI Features

- **Instructions Button**: Click to view setup instructions
- **Flow Selection**: Select which automation flow to run
- **Start/Stop Controls**: Control automation execution
- **Real-time Logs**: See what's happening live
- **Image Preview**: View captured creature icons and map screenshots
- **Always on Top**: GUI stays visible during automation

## Configuration

Edit `config.py` to adjust:

- `MATCH_THRESHOLD` - Image matching confidence (default: 0.6)
- `CLICK_DELAY` - Delay between clicks (default: 0.5s)
- `SEARCH_TIMEOUT` - Max time to search (default: 10s)
- `DEBUG_MODE` - Show detailed debug output (default: True)

## Project Structure

```
tb/
├── automation_launcher.py   # Main GUI launcher
├── automation_engine.py    # Core automation functions
├── image_finder.py         # Image recognition engine
├── config.py               # Configuration settings
├── flow_control.py         # Flow control (stop/start)
├── window_utils.py         # Window management
├── flows/
│   └── Crypts.py           # Crypt automation flow
├── images/
│   └── Crypts/              # Button images for the flow
├── start.bat               # Easy launcher (double-click to run)
└── requirements.txt        # Python dependencies
```

## Troubleshooting

**Issue: Module not found errors**
- Make sure you're using Python 3.12
- Reinstall dependencies: `py -3.12 -m pip install -r requirements.txt`

**Issue: Images not found**
- Check that images are in `images/Crypts/` folder
- Verify image filenames match exactly

**Issue: Wrong button clicked**
- The tool automatically finds the rightmost Explore button
- Check debug output to see which buttons were found

**Issue: Creature not found on map**
- Ensure the game is in windowed mode, not fullscreen
- The tool resizes to 1080x800 automatically
- Make sure Carter is your 1st Captain

**Issue: Speed-ups not working**
- Ensure the Speed-up area is EMPTY before starting
- The tool will use speed-up items automatically

## Advanced Features

### Multi-Scale Matching
The tool automatically tries different scales (80%, 100%, 120%, 140%, 160%) to find creatures on the map regardless of zoom level.

### Center-Area Optimization
Searches only the center 30% of the game window for faster and more accurate creature detection.

### Automatic Cleanup
- Removes captured images on each restart to prevent disk buildup
- Automatically clicks all close buttons if any error occurs before restarting

## License

Free to use and modify.

HAVE FUN!

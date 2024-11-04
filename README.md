# Recruitment Bot

This is an automated recruitment bot that performs recruitment targetting an operator specified by the user. It connects with an emulator via adb and uses OCR to determine the optimal tags for the character, and inputs them in before expediting.

## Features
- Automates recruitment tasks based on tags and priorities.
- Automatically stops recruitment if a six star or five star operator is detected
- (Optional) Automatically prioritizes four star guarantees for yellow certificates if the primary operator's rarity cannot be guaranteed, or or stops recruitment if the Robot tag is detected. Specified by user preferences.

## Requirements
- Python 3.x
- Libraries: `numpy`, `opencv-python`, `pytesseract`
- Emulator with open adb connection

## Usage

### User Specifications
Specify the user preferences in preferences_gen.py. 
1. You enter in the primary operator prioritized, a secondary operator if no relevant tags are present for the first, and whether or not to prioritize 4 star guarantees if the primary target is not found, if whether or not to stop the program
2. Run preferences_gen.py. It will search for the specified name in the recruitment database, and display the tags. If you are satisfied with this, proceed to main.py

### Running the bot
1. Navigate to the following window on the top left recruitment slot of an arknights emulator at resolution 1920x1080.
	a. If you are not at this resolution, you will need to customize parameters for image recognition, found in main.py and in tagbuttons.txt (which outlines the location of tags, used for ocr).

![Screenshot of the Bot in Action](screenshot.png)

2. **Run the bot** using the python script main.py

3. The bot will automatically detect tags, calculate the optimal tags for the prioritized operator, click the tags, select the appropriate timer, hit confirm, and expedite.
	a. If a six star, five star, or one star operator can be guaranteed, the bot stops after displaying possible options, allowing the user to pick the tags specifically

## Customization
You can adjust your preferences by editing preferences_gen.py and generating a new preferences.json.
- **primary_target**: The name of the main operator to be targeted
- **stop_on_robot_tag**: Set this to `true` to stop the bot if the "Robot" tag is found.
- **target_priority_over_four_star**: If true, then ignore 4 star guarantees in hopes of prioritizing the main target. If false, then if there is no guarantee for the rarity of the main target, try a 4 star tag to obtain yellow certificates.

## License
MIT License
# Batch Annotating Images
This uses napari-explorer and napari-ndev plugins written by Tim Monko to annotate images in napari. 

### Python/Environment set up
Unfortunately, the napari bundled installer is more locked down, so you will need to set up napari using the command line.

1. Use the instructions to install mambaforge in the main README.md
2. Open Command Prompt (windows) or Terminal (mac). Copy, paste, and press enter the code
3. `conda create --name ndev-env -c conda-forge python=3.9`
4. follow any yes prompts, do not proceed if there is an error
5. `conda activate ndev-env`
6. `pip install "napari[all]" napari-aicsimageio napari-explorer napari-ndev`
Napari and the necessary packages are now installed.

## Using napari to annotate images
1. In the command prompt type `conda activate ndev-env`. This points the terminal to the correct python environment.
2. In the command prompt type `napari`. This is how you will always load napari to work without coding. 
3. Opening Images: 
    1. In the Plugins menu open "Folder Explorer"
    2. You can browse and filter files in folders
    3. If the file has scenes (such as a multi-tile CZI) then an extra widget will open and allow you to select your scene of interest
    4. Check "Unpack channels as Layers" when using the tile widget to ensure annotation and saving works as expected
4. Labeling Images: 
    1. Press the label button when your image is selected to create a label layer. 
    2. Select the brush tool or press '2'
    3. For each thing you want to classify, paint the label
    4. With each new thing, increase the number for the label
5. Saving annotation pairs: 
    1. In the Plugins menu open "Batch Annotator"
    2. Select the appropriate label and image layers
    3. Browse to the folder where you would like to save the images
    4. Press the button and it will save the images into a re-usable image and label folder 

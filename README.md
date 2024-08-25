## Summary
In this demo, python and matlab were used to display a real-time stream of the following:
1. A point cloud plot showing the approximate locations of people in a room.
2. A range-doppler heatmap visualizing the people in a room.
3. A video feed.

Python was used to parse the binary data from the Radar module into a 2D matrix of values corresponding to different ranges and time.
Matlab was used to provide the GUI to visualiize all the charts at the same time.

## About this project:

    This program records radar data directly through AWR1843BOOST and DCA1000EVM, and parses the bin file data into a range-doppler heatmap in real time.


Prerequisites:

    Software:
        - mmWave Studio 02.01.01.00 
        - Python
        - mmWave Demo Visualizer 3.5.0

    Hardware:
        - Texas Instruments AWR1843 Evaluation Module (the radar to be used)
        - DCA1000EVM
        - two USB to micro-USB cables
        - one ethernet cable

    Python Libraries:
        - matplotlib.pyplot
        - matplotlib.animation
        - numpy


Usage:

    1. Flash the AWR1843BOOST with the bin file in : "C:\ti\mmwave_sdk_03_05_00_04\packages\ti\demo\xwr18xx_mmw_demo.bin"
    2. Change AWR1843 into functional mode: SOP[2:0] = 001
    3. Connect AWR1843BOOST and DCA1000EVM to your computer, and turn it on. Refer to the "DCA1000EVM Data Capture Card User's Guide" online.
    4. Open mmWave

    1. Follow Step 1 to Step 3 of the sGroup_mmWave_CLI_data_capture.docx document in the same folder as this README
    2. Move all the files and folders in this folder (dca1000ev_cli_rdmap_livestream_1fps) into the dollowing folder: "C:\ti\mmwave_studio_02_01_01_00\mmWaveStudio\PostProc\"
    3. Navigate to the mentioned folder in the command line
    3. run the command: ".\sGroup_stream.py"


Note: The frame duration captured by the radar is 500ms. However, it takes time to call the start_frame command, to call the stop_frame command and to parse the data into a range-doppler map. Hence, at best, the rdmap will only stream at 1fps. When the software is running slower than usual, a rate of 1fps cannot even be achieved. Hence, recording real time radar data by repeatedly calling start_record commands to the DCA1000EVM_CLI does not seem feasible in achieving high speeds of radar data livestream.

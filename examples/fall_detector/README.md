# Fall detection with Blazepose on DepthAI

This demo proposes a fall recognition system.

The 3D skeleton of the person is recognized and the positions in which the person may have suffered a fall are indicated.


![Fall detection](medias/fall_detection.gif)

## Usage

```
-> python3 demo.py -h
usage: demo.py [-h] [-e] [-i INPUT] [--pd_m PD_M] [--lm_m LM_M] [-xyz] [-c]
               [--no_smoothing] [-f INTERNAL_FPS]
               [--internal_frame_height INTERNAL_FRAME_HEIGHT] [-s] [-t]
               [--force_detection] [-3 {None,image,mixed,world}]
               [-o OUTPUT]

optional arguments:
  -h, --help            show this help message and exit
  -e, --edge            Use Edge mode (postprocessing runs on the device)

Tracker arguments:
  -i INPUT, --input INPUT
                        'rgb' or 'rgb_laconic' or path to video/image file to
                        use as input (default=rgb)
  --pd_m PD_M           Path to an .blob file for pose detection model
  --lm_m LM_M           Landmark model ('full' or 'lite' or 'heavy') or path
                        to an .blob file
  -xyz, --xyz           Get (x,y,z) coords of reference body keypoint in
                        camera coord system (only for compatible devices)
  -c, --crop            Center crop frames to a square shape before feeding
                        pose detection model
  --no_smoothing        Disable smoothing filter
  -f INTERNAL_FPS, --internal_fps INTERNAL_FPS
                        Fps of internal color camera. Too high value lower NN
                        fps (default= depends on the model)
  --internal_frame_height INTERNAL_FRAME_HEIGHT
                        Internal color camera frame height in pixels
                        (default=640)
  -s, --stats           Print some statistics at exit
  -t, --trace           Print some debug messages
  --force_detection     Force person detection on every frame (never use
                        landmarks from previous frame to determine ROI)

Renderer arguments:
  -3 {None,image,mixed,world}, --show_3d {None,image,mixed,world}
                        Display skeleton in 3d in a separate window. See
                        README for description.
  -o OUTPUT, --output OUTPUT
                        Path to output video file
```

**Examples :**

- Show only the camera visualization whit the fall detector working:

    ```python3 fall_detector.py -e```

- Additionally display the skeleton in 3D:

    ```python3 fall_detector.py -e -3 image```

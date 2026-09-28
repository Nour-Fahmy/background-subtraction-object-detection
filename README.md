# Background Subtraction and Moving Object Detection

A digital image processing project by Nour Waleed. This notebook detects motion in an urban street video with OpenCV's MOG2 background model, cleans foreground masks, and draws bounding boxes around contours.

## Files

- [Google Colab notebook](ImgProj.ipynb) — code and saved examples of masks and detected objects.
- [Project presentation](Background_Subtraction_Portfolio.pdf) — method, challenges, pipeline, and visual results. This public copy removes a student ID from the supplied slides.

## Pipeline

1. Downscale the input video to 640 × 360 pixels and preview a frame.
2. Warm up a MOG2 background model over 80 frames.
3. Apply Gaussian blur, foreground thresholding, morphological opening and closing, then dilation.
4. Find external contours, filter small regions by area, and draw bounding boxes.

The final detection cell uses the lower portion of each frame as its region of interest and displays up to 30 frames. The notebook includes visual examples; it does not provide a quantitative detection benchmark.

## Run in Colab

Upload the source video and change `VIDEO_PATH` (and the earlier video paths) to its location. The supplied notebook expects `/content/19613728-uhd_3840_2160_60fps.mp4`; **the video is not part of these files**. Dependencies are `opencv-python`, `numpy`, and Colab's `cv2_imshow` helper. For a local Python environment, replace `cv2_imshow` with an appropriate display or video writer.

The notebook is presented as submitted. Its intermediate background-mask test warms up MOG2 on a full resized frame and then processes a cropped region, so that section may need adjustment to use the same image dimensions throughout. The final detection cell uses the crop in both warm-up and processing.

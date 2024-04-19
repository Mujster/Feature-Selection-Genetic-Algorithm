# Feature-Selection-Genetic-Algorithm
# Artificial Intelligence

### Dataset: RAVDESS Facial Landmark Tracking Dataset
#### Dataset Url: [RAVDESS Facial Tracking](https://www.kaggle.com/datasets/uwrfkaggler/ravdess-facial-landmark-tracking)

### Introduction:
We implemented a genetic algorithm to select the best features with
maximum fitness to enhance the performance and ability of the Neural
Network to classify ‘happy’ and ‘sad’ emotion. First, we extract files on
the basis of their classification using filename. Each filename is a unique
identifier for its file. We select those files which have emotion code ‘03’
for ‘happy’ and ‘04’ for ‘sad’. Then, by applying genetic algorithm, we
are able to obtain the best features in the file which enhances the ability
of the Neural Network to classify emotions.

### Genetic Operators:
● Fitness Function: We are using the provided neural network model to
obtain the fitness.
● Selection: We are using roulette wheel selection algorithm as in
assignment
● Crossover: We are using a single point crossover algorithm as in
assignment.
● Mutation: We implement mutation function to maintain genetic
diversity.
All these functions are essential to obtain the best selected features


### Dataset:
`File naming convention`
Each of the 7356 RAVDESS files has a unique filename. The filename consists of a 7-part numerical
identifier (e.g., 02-01-06-01-02-01-12.mp4). These identifiers define the stimulus characteristics:
Filename identifiers
##### Modality (01 = full-AV, 02 = video-only, 03 = audio-only).
##### Vocal channel (01 = speech, 02 = song).
##### Emotion (01 = neutral, 02 = calm, 03 = happy, 04 = sad, 05 = angry, 06 = fearful, 07 = disgust, 08 = surprised).
##### Emotional intensity (01 = normal, 02 = strong). NOTE: There is no strong intensity for the 'neutral' emotion.
##### Statement (01 = "Kids are talking by the door", 02 = "Dogs are sitting by the door").
##### Repetition (01 = 1st repetition, 02 = 2nd repetition).
##### Actor (01 to 24. Odd numbered actors are male, even numbered actors are female).
#### Filename example: 02-01-06-01-02-01-12.mp4
1. Video-only (02)
2. Speech (01)
3. Fearful (06)
4. Normal intensity (01)
5. Statement "dogs" (02)
6. 1st Repetition (01)

7. 12th Actor (12)
8. Female, as the actor ID number is even.

RAVDESS Facial Landmark Tracking
This data set contains tracked facial landmark movements from the Ryerson Audio-Visual Database of
Emotional Speech and Song (RAVDESS) [RAVDESS Zenodo page]. Motion tracking of actors' faces was
produced by OpenFace 2.1.0 (Baltrusaitis, T., Zadeh, A., Lim, Y. C., & Morency, L. P., 2018). Tracked
information includes: facial landmark detection, head pose estimation, facial action unit recognition, and
eye-gaze estimation.
url: https://zenodo.org/records/3255102
Tracking results for each trial are provided as individual comma separated value files (CSV format). File
naming convention of tracked files is identical to that of the RAVDESS. For example, tracked file "01-01-
01-01-01-01-01.csv" corresponds to RAVDESS audio-video file "01-01-01-01-01-01-01.mp4".
Tracking File Output Format
This data set retained OpenFace's data output format, described here in detail. The resolution of all input
videos was 1280x720. When tracking output units are in pixels, their range of values is (0,0) (top left
corner) to (1280,720) (bottom right corner).
Columns 1-3 = Timing and Detection Confidence
 1. Frame - The number of the frame (source videos 30 fps), range = 1 to n
 2. Timestamp - Time of frame, range = 0 to m
 3. Confidence - Tracker confidence level in current landmark detection estimate, range = 0 to 1
Columns 4-291 = Eye Gaze Detection
 4-6. gaze_0_x, gaze_0_y, gaze_0_z - Eye gaze direction vector in world coordinates for eye 0
(normalized), eye 0 is the leftmost eye in the image (think of it as a ray going from the left eye in
the image in the direction of the eye gaze).
 7-9. gaze_1_x, gaze_1_y, gaze_1_z - Eye gaze direction vector in world coordinates for eye 1
(normalized), eye 1 is the rightmost eye in the image (think of it as a ray going from the right eye
in the image in the direction of the eye gaze).
 10-11. gaze_angle_x, gaze_angle_y - Eye gaze direction in radians in world coordinates,
averaged for both eyes. If a person is looking left-right this will results in the change of
gaze_angle_x (from positive to negative) and, if a person is looking up-down this will result in
change of gaze_angle_y (from negative to positive), if a person is looking straight ahead both of
the angles will be close to 0 (within measurement error).

 12-123. eye_lmk_x_0, ..., eye_lmk_x55, eye_lmk_y_0,..., eye_lmk_y_55 - Location of 2D eye
region landmarks in pixels. A figure describing the landmark index can be found here.
 124-291. eye_lmk_X_0, ..., eye_lmk_X55, eye_lmk_Y_0,..., eye_lmk_Y_55,..., eye_lmk_Z_0,...,
eye_lmk_Z_55 - Location of 3D eye region landmarks in millimeters. A figure describing the
landmark index can be found here.
Columns 292-297 = Head pose
 292-294. pose_Tx, pose_Ty, pose_Tz - Location of the head with respect to camera in
millimeters (positive Z is away from the camera).
 295-297. pose_Rx, pose_Ry, pose_Rz - Rotation of the head in radians around X,Y,Z axes with
the convention R = Rx * Ry * Rz, left-handed positive sign. This can be seen as pitch (Rx), yaw
(Ry), and roll (Rz). The rotation is in world coordinates with the camera being located at the
origin.
Columns 298-433 = Facial Landmarks locations in 2D
 298-433. x_0, ..., x_67, y_0,...y_67 - Location of 2D landmarks in pixels. A figure describing the
landmark index can be found here.
Columns 434-637 = Facial Landmarks locations in 3D
 434-637. X_0, ..., X_67, Y_0,..., Y_67, Z_0,..., Z_67 - Location of 3D landmarks in millimetres.
A figure describing the landmark index can be found here. For these values to be accurate,
OpenFace needs to have good estimates for fx,fy,cx,cy.
Columns 638-677 = Rigid and non-rigid shape parameters
Parameters of a point distribution model (PDM) that describe the rigid face shape (location, scale and
rotation) and non-rigid face shape (deformation due to expression and identity). For more details, please
refer to chapter 4.2 of my Tadas Baltrusaitis's PhD thesis [download link].
 638-643. p_scale, p_rx, p_ry, p_rz, p_tx, p_ty - Scale, rotation, and translation terms of the PDM.
 644-677. p_0, ..., p_33 - Non-rigid shape parameters.
Columns 687-712 = Facial Action Units
Facial Action Units (AUs) are a way to describe human facial movements (Ekman, Friesen, and Hager,
2002) [wiki link]. More information on OpenFace's implementation of AUs can be found here.
 678-694. AU01_r, AU02_r, AU04_r, AU05_r, AU06_r, AU07_r, AU09_r, AU10_r, AU12_r,
AU14_r, AU15_r, AU17_r, AU20_r, AU23_r, AU25_r, AU26_r, AU45_r - Intensity of AU
movement, range from 0 (no muscle contraction) to 5 (maximal muscle contraction).

 695-712. AU01_c, AU02_c, AU04_c, AU05_c, AU06_c, AU07_c, AU09_c, AU10_c, AU12_c,
AU14_c, AU15_c, AU17_c, AU20_c, AU23_c, AU25_c, AU26_c, AU28_c, AU45_c - Presence
or absence of 18 AUs, range 0 (absent, not detected) to 1 (present, detected).
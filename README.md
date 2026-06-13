EchoNet-Dynamic:
Interpretable AI for beat-to-beat cardiac function assessment

EchoNet-Dynamic is a end-to-end beat-to-beat deep learning model for

    semantic segmentation of the left ventricle
    prediction of ejection fraction by entire video or subsampled clips, and
    assessment of cardiomyopathy with reduced ejection fraction.
Dataset

A deidentified set of 10,030 echocardiogram images which were used for training EchoNet-Dynamic. Preprocessing of these images, including deidentification and conversion from DICOM format to AVI format videos, were performed with OpenCV and pydicom. Additional information is at https://echonet.github.io/dynamic/. These deidentified images are shared with a non-commerical data use agreement.
Usage
Preprocessing DICOM Videos

The input of EchoNet-Dynamic is an apical-4-chamber view echocardiogram video of any length. The easiest way to run our code is to use videos from our dataset, but we also provide a Jupyter Notebook, ConvertDICOMToAVI.ipynb, to convert DICOM files to AVI files used for input to EchoNet-Dynamic. The Notebook deidentifies the video by cropping out information outside of the ultrasound sector, resizes the input video, and saves the video in AVI format.
Setting Path to Data

By default, EchoNet-Dynamic assumes that a copy of the data is saved in a folder named a4c-video-dir/ in this directory. This path can be changed by creating a configuration file named echonet.cfg (an example configuration file is example.cfg).
Running Code

EchoNet-Dynamic has three main components: segmenting the left ventricle, predicting ejection fraction from subsampled clips, and assessing cardiomyopathy with beat-by-beat predictions. Each of these components can be run with reasonable choices of hyperparameters with the scripts below. We describe our full hyperparameter sweep in the next section.
Prediction of Ejection Fraction from Subsampled Clips

echonet video

This creates a directory named output/video/r2plus1d_18_32_2_pretrained/, which will contain

    log.csv: training and validation losses
    best.pt: checkpoint of weights for the model with the lowest validation loss
    test_predictions.csv: ejection fraction prediction for subsampled clips

Beat-by-beat Prediction of Ejection Fraction from Full Video and Assesment of Cardiomyopathy

The final beat-by-beat prediction and analysis is performed with scripts/beat_analysis.R. This script combines the results from segmentation output in size.csv and the clip-level ejection fraction prediction in test_predictions.csv. The beginning of each systolic phase is detected by using the peak detection algorithm from scipy (scipy.signal.find_peaks) and a video clip centered around the beat is used for beat-by-beat prediction.
Hyperparameter Sweeps

The full set of hyperparameter sweeps from the paper can be run via run_experiments.sh. In particular, we choose between pretrained and random initialization for the weights, the model (selected from r2plus1d_18, r3d_18, and mc3_18), the length of the video (1, 4, 8, 16, 32, 64, and 96 frames), and the sampling period (1, 2, 4, 6, and 8 frames).

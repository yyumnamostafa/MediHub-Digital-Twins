EchoNet-Dynamic Demo App
A web demo I built (with Gradio) that provides an easy interface for running the published EchoNet-Dynamic model on echocardiogram videos to assess cardiac function (left-ventricle segmentation and ejection-fraction prediction).
What it does
EchoNet-Dynamic performs semantic segmentation of the left ventricle and predicts ejection fraction from echocardiogram video. This app wraps that model in a simple interface so a user can run inference without setting up the full pipeline. The demo/interface code is my contribution; the model and underlying research are not mine (see credit below).
Data
This demo uses the EchoNet-Dynamic model; it does not redistribute the original dataset, which is shared by the authors under a non-commercial data use agreement (https://echonet.github.io/dynamic/).
Credit
All model and research credit goes to the EchoNet-Dynamic authors: Ouyang et al., "Video-based AI for beat-to-beat assessment of cardiac function," Nature, 2020 (https://doi.org/10.1038/s41586-020-2145-8). Original repository: https://github.com/echonet/dynamic.

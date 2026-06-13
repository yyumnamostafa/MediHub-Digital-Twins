A web demo I built (with Gradio) that provides an easy interface for running the published EchoNet-Dynamic model on echocardiogram videos to assess cardiac function (left-ventricle segmentation and ejection-fraction prediction).
What it does
EchoNet-Dynamic performs semantic segmentation of the left ventricle and predicts ejection fraction from echocardiogram video. This app wraps that model in a simple interface so a user can run inference without setting up the full pipeline.
Data
This demo uses the EchoNet-Dynamic model; it does not redistribute the original dataset, which is shared by the authors under a non-commercial data use agreement (https://echonet.github.io/dynamic/).
Credit
All model and research credit goes to the EchoNet-Dynamic authors. See the paper and original repository linked above.

# Lab 1 - Gemini: a Real-time Video Analytics System with Dual Computing Resource

### Overview (Abstract)

Useing dual FPGA images to swap between CPU and GPU images for processing. 
### Sections to understand - II - Motivation
## A) Background on RT video analytics
> - Perform analytics on pre-trained NN to recognize sptial or temporal events in a video stream with latency reqs. 
> - Preproc a frame and select the appropriate NN model to optizmize accuracy and latency. 

```IIC``` - Instruction-intensive computing
```DIC``` - Data-intenstive computing
## Order of ops
### First
1) ```Execution config sub-module``` (ECM) which video reolution selection module to resize the resolution of a frame
2) Also a ```NN selection sub-module``` to select the best NN model for best accuracy and delay

### Second
1) This frame is sent to ```frame filtering/ROI extraction module``` to filter out the frame if it doesn't contain any relevant information or to extract the ```Region of Interest``` (ROI) from the frame. (Background subtraction and object cropping techs.)

### Final
1) This preprocessed frame and NN model are sent to the ```Model Inference Module``` to execute analysis and output results.

### In the field
> - Typically edge devices contain a CPU and GPU. 
Exmaples:
1) ```Microsoft Vision Zero``` used a webcam
2) ```Azure Stack Edge``` with ```Intel Xeon CPU``` and ```Nvidia T4 Tensor```

The CPU handles the first two stages of the RT Video Analytics Pipeline
The final stage is handled by the GPU (Model inference)

## B) Motivation
Include Fig 2. Discuss the Accuracy at the difference times. 
Dawn - 85.7%
Rush - 65.2%
Midnight - 63.6%

Table 1 Shows the Model selection, CPU/GPU util, resolution, filter rate.
Filter rate increases as vehicle count decreases, this is because frame differences are greater and fewer frames are filtered out.

More frames filtered out, lower GPU util since the NN is utilized less often.

More frames being fed to the GPU the resolution was lowered and a different model was selected. 

Table 1 shows the optimal model and resolution selected.

Different contents can result in dynamic IIC and DIC

Notice, GPU util is high but CPU util is low. In the field, resources are fixed. Limits ability to adapt to workloads.

## C) Dual-Image FPGA and Potential Approach
Typically, a single FPGA image is used and flashing a new image takes minutes which isn't optimal.

New tech allows for a second image (Dual-Image FPGA) to store it's second image in the User Flash Memory (UFM)
To promote switching with low latency (9ms on Intel Max10)

Allows for image switching from CPU image (For IIC) to the GPU image (DIC).

## FPGA Time Allocation Strategcy for 1 s periods

CG-x%-y% (CPU/GPU util %)

With Table II we can observe the resource utilization / accuracy relation for the different times. (Dawn/Rush/Midnight)

Note, the midnight CG-x%-y% requires a large CPU x% resource allocation to handle the frame fitlering of the higher reolution frames, which is done on the CPU. 
SPECULATION: **Potentially, a higher accuracy could be achived with lower CPU util if the frame was a lower resolution**

## III Design Overview
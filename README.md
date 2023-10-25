## SUM : Segmentation with U-Net and Mammogram images

### 1. Introduction
Breast cancer is a major global health concern. Early detection is crucial, and medical imaging, particularly mammography, plays a key role. It allows radiologists to visualize and assess breast tissue for abnormalities, like tumors.

Segmenting mammogram images, i.e., delineating regions of interest (tumors) from surrounding tissue, is vital for diagnosis and treatment planning. The U-Net architecture, known for its precision in medical image segmentation, is well-suited for this task.

### 2. U-Net
#### Encoder
- The Encoder’s purpose is to extract high-level features from the input image by reducing its size and increasing the number of features.
- The input is a grayscale image of size 1024x1024 pixels.
- The image goes through a series of convolutional layers. In the beginning, 32 filters are applied, leading to an output with 32 channels. Next, convolutional layers with 64 filters are used, resulting in an output with 64 channels.
- Max Pooling is applied to downsample the image, reducing its size. This helps capture global context and important high-level features.

#### Decoder
- The Decoder’s goal is to restore the original image’s spatial resolution (1024x1024) while reducing the number of channels.
- Each upsampling layer in the Decoder is connected with the corresponding layer in the Encoder using a skip connection. This helps combine local and global features for accurate predictions
- The image from the Encoder is passed through transposed convolutional layers to increase its size (upsampling). This ensures that the segmentation map matches the original image’s dimensions
- A 1x1 convolutional layer is then applied to reduce the number of channels while retaining crucial information. The final output has three channels, each representing the probability of “normal”, “benign” and “malignant"

![image](https://github.com/smruthi49/SUM/assets/94833021/2413f17c-a628-4a1a-9358-963e30c9f222)


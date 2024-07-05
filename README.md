# Human-Action-Recognition
This repository contains the implementation details and architectures of Convolutional Long Short-Term Memory (ConvLSTM) and Long-term Recurrent Convolutional Networks (LRCN) models. Below are descriptions of the key components and visual representations used in these models.

Overview
Both ConvLSTM and LRCN models are designed to handle spatiotemporal data, such as video sequences or any data where spatial and temporal dimensions are important. ConvLSTM integrates convolutional operations into LSTM units, while LRCN combines convolutional neural networks (CNNs) with recurrent neural networks (RNNs) for end-to-end learning.

ConvLSTM Architecture
![ConvLSTM Architectur](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/ba9655f6-b0a4-471d-a2bf-49844c9f03e2)
ConvLSTM Cell

The above diagram illustrates the inner workings of a ConvLSTM cell. Key components include:

Input Gate (I_t): Controls how much of the new information from the input will be used.
Forget Gate (F_t): Decides what information from the previous cell state (C_{t-1}) should be forgotten.
Output Gate (O_t): Determines the output at the current time step (H_t).
Cell State (C_t): Maintains the state information across different time steps.
Hidden State (H_t): The output of the cell which also serves as an input to the next time step.
The ConvLSTM cell uses convolutional operations for the gates instead of fully connected layers, allowing it to capture spatial features effectively.

Model Structure
![convlstm_model_structure_plot](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/c89f95ef-c280-4ad5-8508-a78901d12838)

This flowchart depicts the structure of the ConvLSTM model used. The key layers include:

ConvLSTM2D Layers: These layers apply convolutional operations followed by LSTM units, capturing spatiotemporal features.
MaxPooling3D Layers: These layers reduce the spatial dimensions, helping in downsampling the input and reducing computational load.
TimeDistributed Layers: These layers apply a layer (e.g., Dropout) to every temporal slice of an input.
Flatten Layer: This layer flattens the input to a 1D array, preparing it for the dense layer.
Dense Layer: The final dense layer is used for the output, which in this case, has 4 units.
The model takes input data of shape (None, 20, 64, 64, 3) where:

20: Number of time steps.
64x64: Spatial dimensions of the input.
3: Number of channels (e.g., RGB for images).
The final output has 4 units, which can be interpreted based on the specific use case (e.g., classification into 4 categories).
![ConvLSTM Total loss Vs Validation Loss](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/492aa207-ffe3-4047-88d4-62e95029fe58)
![ConvLSTM Total Accuracy Vs Validation Accuracy](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/d6e25c47-c3d9-463b-87e3-fbaa3d8727ed)

LRCN Architecture
![LRCN Architecture](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/6fd67606-6357-4e30-81e7-665d33fae38c)
The model architecture comprises the following main components:

Input Layer: The input is a sequence of images depicting a yoga pose.
Convolutional Layers: These layers extract spatial features from the input images. Each image in the sequence is processed by the convolutional layers independently.
LSTM Layers: The extracted features are then fed into LSTM units that capture the temporal dependencies between the frames in the sequence.
Output Layer: The final dense layer provides the classification result, predicting the type of yoga pose depicted in the input sequence.

Model Structure
![LRCN_model_structure_plot](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/eaeffaa6-e85f-4242-9f2a-77d3884f2202)

This flowchart depicts the structure of the LRCN model used. The key layers include:

TimeDistributed Conv2D Layers: These layers apply convolutional operations to each frame individually.
TimeDistributed MaxPooling2D Layers: These layers reduce the spatial dimensions of each frame.
TimeDistributed Dropout Layers: These layers apply dropout to prevent overfitting.
TimeDistributed Flatten Layer: This layer flattens the input to a 1D array for each time step.
LSTM Layer: This layer captures the temporal dependencies across frames.
Dense Layer: The final dense layer is used for the output, which in this case, has 4 units.
The model takes input data of shape (None, 20, 64, 64, 3) where:

20: Number of time steps.
64x64: Spatial dimensions of the input.
3: Number of channels (e.g., RGB for images).
The final output has 4 units, which can be interpreted based on the specific use case (e.g., classification into 4 categories).

![LRCN Total loss Vs Validation Loss](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/30035b75-f59c-4fbe-af2d-368d45deabdf)
![LRCN Total Accuracy Vs Validation Accuracy](https://github.com/YashRaval201/Human-Action-Recognition/assets/70638712/cb517b17-6400-4b30-a5f1-b3ce4c82f80d)

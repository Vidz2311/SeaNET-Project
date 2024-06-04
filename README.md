# SeaNET-Project
This project provides the code and results for "Lightweight Salient Object Detection in Optical Remote-Sensing Images via Semantic Matching and Edge Alignment", IEEE TGRS, 2023.


Requirements
Python 3.7+
PyTorch 1.9.0+
NumPy
Pillow
SciPy
Imageio
Saliency Maps
We provide saliency maps of our SeaNet on ORSSD, EORSSD, and additional ORSI-4199 datasets in ./models/saliency_maps.zip.



Training
We use data_aug.m for data augmentation.

Modify paths of datasets in train_SeaNet.py.
Run train_SeaNet.py.
Note: Our main model is under ./model/SeaNet_models.py.

Pre-trained Model and Testing
We provide the pre-trained models in ./models/.
Modify paths of pre-trained models and datasets.
Run test_SeaNet.py.
Evaluation Tool
You can use the evaluation tool (MATLAB version) to evaluate the above saliency maps.

Running with Docker
Prerequisites
Docker installed on your system.
(Optional) NVIDIA GPU with drivers and NVIDIA Docker runtime for GPU support.
Docker Setup
Create a Dockerfile: Place the following Dockerfile in the root of your project directory (C:\Users\Vidhya\getting-started-app\SeaNet-main).

Dockerfile
Copy code
# Use the official PyTorch image with CUDA support as the base image
FROM pytorch/pytorch:latest

# Set the working directory inside the container
WORKDIR /app

# Copy the entire project folder into the container
COPY . /app

# Install any additional dependencies
RUN pip install torchvision scipy imageio

# Command to run the training script
CMD ["python", "train_SeaNet.py"]
Build the Docker Image:

bash
Copy code
docker build -t project_image .
Run the Docker Container:

Without GPU Support:

bash
Copy code
docker run -it project_image
With GPU Support (requires NVIDIA GPU and NVIDIA Docker runtime):

bash
Copy code
docker run --gpus all -it project_image
Modifications for CPU-only Systems
If you're running on a system without an NVIDIA GPU, ensure your code does not attempt to use CUDA. Modify train_SeaNet.py to avoid setting CUDA devices:

python
Copy code
# Comment out or remove the line that sets the CUDA device
# torch.cuda.set_device(0)

Contact
If you encounter any problems with the code, want to report bugs, etc., please contact me at:
Vidya2000singh@gmail.com
tusharmondal05032003@gmail.com
sumit686856@gmail.com
ashutosh4u4all@gmail.com

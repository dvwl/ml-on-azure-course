---
lab:
    title: 'Train Production Model'
---
## Module 12: Use AutoML to train a labeled dataset and develop a production model

### Prepare the Jupyter notebook workspace
The Azure Machine Learning compute instance is a secure, cloud-based Azure workstation that provides data scientists with a Jupyter Notebook server, JupyterLab, and a fully managed machine learning environment. Previously we deployed a compute instance that we'll now use to execute a special notebook. This notebook will allow us to train our object detection model using AutoML. In this unit, we'll prepare the Jupyter notebook workspace with prerequisites that will allow us to run the notebook successfully.

#### Prepare the Jupyter notebook workspace
1. Sign in to [Azure Machine Learning studio](https://ml.azure.com/), and select your workspace.

1. If you have already saved and are able to retrieve the config.json file from Module 10, you can skip the next two steps. If you need to obtain this file again, open the [Azure Portal](https://portal.azure.com/) in a new tab and navigate to your Azure Machine Learning resource. You can easily locate this resource by typing “Azure Machine Learning” in the Azure search bar and choosing the Machine Learning icon. This action will list all available Azure Machine Learning resources in your Azure Subscription.

    ![Find Resource](../images/12/2-find-resource.png)

1. When you've successfully navigated to your Azure Machine Learning resource, notice in the Overview section there will be a button labeled "Download config.json". Select this button to download the configuration and store it somewhere secure and accessible so that it may be used in upcoming steps.

    ![Download Config](../images/12/2-download-config.png)

1. On the left-hand pane, locate the **Manage** section and select **Compute**, then select the **Jupyter** link that corresponds to the earlier deployed compute instance.

    ![Open Jupyter Instance](../images/12/2-open-jupyter-instance.png)

1. Select the **Users** directory, then select your username.

    ![Select User Directory](../images/12/2-select-user-directory.png)

1. Download and extract the following provided [Jupyter workspace files](https://github.com/microsoft/Develop-Custom-Object-Detection-Models-with-NVIDIA-and-Azure-ML-Studio/raw/main/jupyter_workspace_compressed.zip). You'll need to decompress the included *jupyter_workspace_compressed.zip* file as the included files will be referenced in the next step.

1. We'll now upload the prerequisite files and create a folder location in our workspace:

    1. Select the **Upload** button (top right) and upload the *config.json* file that was obtained in previous steps (this file isn't included in the .zip file, this file was obtained earlier in the Azure portal and is unique to your account).

    1. Select the *Upload* button (top right) and upload the *test_image1.jpg* file.

    1. Select the *Upload* button (top right) and upload the *yolo_onnx_preprocessing_utils.py* python script.

    1. Select the Upload button (top right) and upload the AutoMLImage_ObjectDetection.ipynb Jupyter notebook.

    The final view of the workspace should look like the following:

    ![Jupyter Workspace](../images/12/2-jupyter-workspace.png)

### Configure the Jupyter notebook execution environment
In this section, we'll work with the Jupyter notebook that was uploaded to our Jupyter workspace. We'll execute commands that will install dependencies to ensure that our environment can run later referenced AutoML tasks. This process will involve upgrading the [azureml Python SDK](https://pypi.org/project/azureml-sdk/) and installing the [torchvision](https://pypi.org/project/torchvision/) Python package.

#### Configure the Jupyter notebook execution environment
1. Navigate to your Jupyter workspace and select the *AutoMLImage_ObjectDetection.ipynb* file to open the Jupyter notebook.

    ![Open Notebook](../images/12/3-open-notebook.png)

1. If you receive a **Kernel not found** prompt, select **Python 3.8 - AzureML** from the dropdown as shown then select Set Kernel.

    ![Set Kernel](../images/12/3-set-kernel.png)

1. Execute the cells in the **Environment Setup** section. This can be done by selecting the cell, then pressing Shift+Enter on the keyboard. Repeat this process for each cell and stop after running `pip install torchvision==0.9.1`.

    ![Environment Setup](../images/12/3-environment-setup.png)

1. After you've successfully executed the **pip install torchvision==0.9.1** task, you'll need to restart the Kernel. To restart the kernel, select the **Kernel** menu item and choose **Restart** from the dropdown.

    ![Restart Kernel](../images/12/3-restart-kernel.png)

1. Execute the **pip freeze* cell, which will list all installed python libraries, then execute the cell underneath it to import the libraries that will be used in further steps.

1. Continue to execute the cells in the **Workspace setup** section. This step will read in the config.json file that was uploaded earlier and allow us to execute tasks against your Azure Machine Learning workspace.

1. Continue to execute the cells in the **Compute target setup** section. You'll want to change the value of **compute_name** to match the name of the compute instance that exists in your Azure Machine Learning studio workspace. Otherwise, this script may either fail to create the instance (if an instance of the same name already exists in the same region) or it will create a second instance (the subsequent steps will still work but it will not use the existing resource).

    ![Compute Target Setup](../images/12/3-compute-target-setup.png)

1. Continue to execute the cells in the **Experiment Setup** section. This will create an Azure machine learning experiment that will allow us to track the status of the model during training.

1. Continue to execute the cells in the **Dataset with input Training Data** section. Please note that you'll need to replace the name variable with the name of the Dataset that was exported at the end of the previous module. This value can be obtained in your Azure Machine Learning studio instance in the left-hand pane, locate the Assets section and select **Datasets**. You can validate that the Dataset was imported properly by viewing the output in the **training_dataset.to_pandas_dataframe()** cell.

    ![Dataset Name](../images/12/3-dataset-name.png)

    ![Dataset Training Data](../images/12/3-dataset-training-data.png)


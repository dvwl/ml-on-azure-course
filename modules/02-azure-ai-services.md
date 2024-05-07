---
lab:
    title: 'Get Started with Azure AI Services'
---
## Module 2: Getting Started with Azure AI Services

In Module 2, you'll kickstart your journey with Azure AI Services by creating an Azure AI Services resource in your Azure subscription and utilizing it from a client application. The primary goal of this exercise is to familiarize yourself with a general pattern for provisioning and working with Azure AI services as a developer. Whether you prefer C# or Python, you'll have the opportunity to engage with the Azure AI Services.

### Explore Azure AI Module

To begin your exploration of Azure AI Services, we recommend diving into the module provided by Microsoft Learning:

- ~~**Azure AI Services:** [Getting Started with Azure AI Services](https://microsoftlearning.github.io/mslearn-ai-services/Instructions/Exercises/01-use-azure-ai-services.html)~~

- Custom Vision AI: [Custom Vision Portal](https://www.customvision.ai/)

~~This module offers a hands-on experience in provisioning Azure AI resources and demonstrates how to interact with them from a client application using either C# or Python. While the focus is not on gaining expertise in any particular service, you'll gain valuable insights into the development workflow and best practices for integrating Azure AI Services into your projects.~~

In this module, we'll use the provision an Azure AI Service and connect that to Custom Vision Portal.

We'll use the following parameters for this module:
Name: insert your unique name
Description: this is optional
Resource: select your resource from earlier modules
Project Types: Object Detection
Domains: General (compact) \[S1\] or General \[A1\]

NOTE: If you want to export the model to TensorFlow, CoreML, ONNX, you may experiment with General (compact).

We'll upload the images in the [training-images folder](../images/02/training-images/) to the Custom Vision for Object Detection, label / tag them, train the model, and run the model with images from the [predict-images folder](../images/02/test-images/). 

Feel free to use your own images when testing the model. Also, feel free to purposely mislabel the objects, example, tagging apples as banana, just to confuse the model and observe the output.

### Next Steps

After completing Module 2, you'll be equipped with the foundational knowledge to start building intelligent applications using Azure AI Services. Stay tuned for further modules where we'll explore advanced AI capabilities and real-world use cases.

Happy coding!
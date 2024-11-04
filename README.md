# Finetuned-Flan-T5-Base-For-Medical-Chatbot
Using the pre-trained Flan-T5-Base model from HuggingFace, I fine tuned it to be capable of becoming a medical chatbot to answer medical related query. From not being able to answer any medical query at all, after finetuning, the model is capable of answering medical questions when asked! Observe the huge difference between the output of the original model vs the finetuned model! (UI is auto generated using Gradle, more details below)
![image](https://github.com/user-attachments/assets/64724850-bbf1-4941-b33d-b44e9e387454)

# Dataset:
Dataset Source is from: https://www.kaggle.com/datasets/saifulislamsarfaraz/medical-chatbot-dataset. Minor preprocessing have been done to the dataset by removing all rows with label -1 as this indicates that the medical question has not been answered properly

# Why fine tune Flan-T5-Base?
### Pre-trained on Instruction-based Tasks: 
Flan-T5 is part of the Flan series, which is specifically fine-tuned on instruction-based datasets. This means it has a foundational ability to understand instructions and respond appropriately, making it especially adaptable for a task like a medical chatbot where it needs to provide clear and concise answers to queries.

### Balanced Size and Efficiency: 
With around 250 million parameters, Flan-T5-Base is small enough to be fine-tuned efficiently on a modest hardware setup yet large enough to capture complex patterns in medical data. This makes it ideal for applications needing both accuracy and speed, particularly in real-time chat scenarios.

### Cost-effective and Practical for Deployment: 
Given its lightweight nature, Flan-T5-Base is less resource-intensive, which translates to lower deployment costs and quicker response times. This is especially important for healthcare applications where scaling to handle large volumes of queries while minimizing costs is essential.

# Details:
In this project, I finetune the model with 2 methods, 1st being without QLoRA where we fine tune all of the 250M parameters and the 2nd being with QLoRA where only around 0.53% of the total parameters of the quantized model is finetuned, making it even less resource intensive. The models are then evaluated using ROUGE and BLEU Metrics 

### Ending results for finetuning without QLoRA:
![image](https://github.com/user-attachments/assets/b56c2d3d-b255-483d-8e82-9aeb1cc35ec6)

### Ending results for finetuning with QLoRA:
![image](https://github.com/user-attachments/assets/9d9175fc-ced4-42f4-a11b-42f09ff0bfc0)

Both shows a massive improvement in terms of ROGUE and BLEU Metrics that we use to evaluate the capability of the finetuned model. There is a tradeoff whereby if we finetuned with QLoRA, it is less resource intensive to train but it is less accurate while without QLoRA, it is much more resource intensive but is is much more accurate

I have also added a code that utilize the Gradle library that will automate the production of the frontend, providing us with a clean UI to test our model. The sample of the UI can be seen from the very first image!






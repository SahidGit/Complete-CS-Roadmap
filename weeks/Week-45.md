# 🔥 Week 45: PyTorch & TensorFlow Deep Learning Frameworks

> **Duration:** 24 hours | **Difficulty:** 🔴 Advanced | **Prerequisites:** Week 44

## 🎯 Goal

Master PyTorch and TensorFlow frameworks for building production-grade deep learning models. Learn GPU acceleration, dataset handling, and model deployment.

## 🎓 Learning Objectives

By the end of this week, you will:
- ✅ Master PyTorch fundamentals
- ✅ Master TensorFlow/Keras
- ✅ Handle large datasets efficiently
- ✅ Utilize GPU acceleration
- ✅ Implement transfer learning
- ✅ Save and load models
- ✅ Debug and profile models
- ✅ Deploy models in production

## 📚 Core Concepts

### PyTorch Tensors

```python
import torch
import torch.nn as nn

# Tensor creation
x = torch.tensor([1.0, 2.0, 3.0])
x = torch.randn(3, 4)  # Random normal
x = torch.zeros(3, 4)  # Zeros
x = torch.ones(3, 4)   # Ones

# GPU acceleration
if torch.cuda.is_available():
    x = x.cuda()  # Move to GPU
    x = x.to('cuda')

# Autograd
x = torch.tensor([2.0, 3.0], requires_grad=True)
y = x ** 2
z = y.sum()
z.backward()  # Compute gradients
print(x.grad)  # Gradients
```

### PyTorch Neural Network

```python
import torch.nn as nn
import torch.optim as optim

class CNN(nn.Module):
    def __init__(self):
        super(CNN, self).__init__()
        self.conv1 = nn.Conv2d(3, 32, kernel_size=3, padding=1)
        self.relu = nn.ReLU()
        self.pool = nn.MaxPool2d(2, 2)
        self.fc1 = nn.Linear(32 * 16 * 16, 128)
        self.fc2 = nn.Linear(128, 10)
    
    def forward(self, x):
        x = self.conv1(x)
        x = self.relu(x)
        x = self.pool(x)
        x = x.view(x.size(0), -1)
        x = self.fc1(x)
        x = self.relu(x)
        x = self.fc2(x)
        return x

# Initialize model
model = CNN()
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=0.001)

# Training loop
for epoch in range(10):
    for images, labels in train_loader:
        # Forward pass
        outputs = model(images)
        loss = criterion(outputs, labels)
        
        # Backward pass
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
```

### TensorFlow/Keras

```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

# Build model
model = keras.Sequential([
    layers.Conv2D(32, (3, 3), activation='relu', input_shape=(28, 28, 1)),
    layers.MaxPooling2D((2, 2)),
    layers.Conv2D(64, (3, 3), activation='relu'),
    layers.MaxPooling2D((2, 2)),
    layers.Flatten(),
    layers.Dense(128, activation='relu'),
    layers.Dropout(0.5),
    layers.Dense(10, activation='softmax')
])

# Compile
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)

# Train
model.fit(x_train, y_train, epochs=10, batch_size=32, validation_split=0.2)

# Evaluate
test_loss, test_acc = model.evaluate(x_test, y_test)
```

### Transfer Learning

```python
import torchvision.models as models
import torch.nn as nn

# Load pre-trained model
resnet = models.resnet50(pretrained=True)

# Freeze early layers
for param in resnet.parameters():
    param.requires_grad = False

# Replace final layer
num_ftrs = resnet.fc.in_features
resnet.fc = nn.Linear(num_ftrs, 10)  # 10 classes

# Only train final layer
optimizer = torch.optim.SGD(resnet.fc.parameters(), lr=0.01)
```

### Dataset Handling

```python
from torch.utils.data import Dataset, DataLoader

class CustomDataset(Dataset):
    def __init__(self, images, labels, transforms=None):
        self.images = images
        self.labels = labels
        self.transforms = transforms
    
    def __len__(self):
        return len(self.images)
    
    def __getitem__(self, idx):
        image = self.images[idx]
        label = self.labels[idx]
        
        if self.transforms:
            image = self.transforms(image)
        
        return image, label

# Create data loader
data_loader = DataLoader(
    dataset,
    batch_size=32,
    shuffle=True,
    num_workers=4
)
```

## 💻 Mini Projects

### Project 1: Image Recognition with Transfer Learning
**Duration:** 4 hours | **Difficulty:** 🔴 Advanced

#### Features
1. ResNet/VGG fine-tuning
2. Data augmentation
3. Learning rate scheduling
4. Model checkpointing
5. Inference pipeline

### Project 2: Flower Classifier
**Duration:** 4 hours | **Difficulty:** 🔴 Advanced

#### Features
1. Dataset creation
2. Model training
3. Hyperparameter tuning
4. Confusion matrix
5. Deployment

### Project 3: Object Detection
**Duration:** 3 hours | **Difficulty:** 🔴 Advanced

#### Features
1. YOLO or SSD
2. Bounding box prediction
3. NMS
4. Real-time inference
5. Video processing

## ✅ Weekly Checklist

- [ ] Master PyTorch tensors and autograd
- [ ] Build PyTorch neural networks
- [ ] Use TensorFlow/Keras effectively
- [ ] Implement transfer learning
- [ ] Handle datasets with DataLoader
- [ ] GPU acceleration working
- [ ] Complete 3 framework projects
- [ ] Ready for Week 46 (NLP)

---

**Next:** [Week 46 - Natural Language Processing 📝](Week-46.md)

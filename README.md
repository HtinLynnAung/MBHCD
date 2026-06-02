# Modified Burmese Handwriting Character Dataset (MBHCD)

This repository contains the official implementation and dataset for our paper submitted to IJDAR.

## 📊 Dataset Specifications
- **Total Classes:** 43 (33 Consonants + 10 Digits)
- **Input Dimensions:** 32x32 pixels (Grayscale)
- **Normalization:** Formatted into `[-1, 1]` range.

## 📥 Download Dataset
You can download the compiled pickle dataset file from the [Releases](../../releases) tab (`bhcd_data.zip`).

## ⚙️ How to Load Data (PyTorch)
```python
import pickle
import torch

pickle_file = './datasets/bhcd_data.pickle'
with open(pickle_file, 'rb') as f:
    data = pickle.load(f)
    X_train = torch.FloatTensor(data['train_dataset']).unsqueeze(1)
    y_train = torch.LongTensor(data['train_labels'])

print('Training set dimensions:', X_train.shape, y_train.shape)
# Output: Training set torch.Size([7009, 1, 32, 32]) torch.Size([7009])

class_map = data['class_mapping']
index_to_burmese = {idx: info['char'] for idx, info in class_map.items()}
total_mapped_classes = len(index_to_burmese)
print(f"📌 Total classes defined in mapping: {total_mapped_classes}")
📌 Total classes defined in mapping: 43
📌 Total unique classes in y_train : 43
📌 Total unique classes in y_test  : 43

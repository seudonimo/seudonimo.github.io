---
title: Model Download from HuggingFace
author: seudonimo
date: 2024-10-19 00:34:00 +0800
categories: [Blogging, Note]
tags: [Huggingface, Aimet-model-zoo, MobileBert, Transformers, PyTorch, ONNX, Tensorflow, TFLite]
---


# Model 추출
Model Download from HuggingFace, and AIMET

## 1. HuggingFace Model 추출

```python
import torch
from transformers import MobileBertModel

# MobileBERT 모델 로드
model = MobileBertModel.from_pretrained("google/mobilebert-uncased")
model.eval()

# 첫 번째 입력: int64 (토큰 인덱스)
dummy_input_1 = torch.randint(0, 30522, (1, 128), dtype=torch.int64)  # 첫 번째 입력, 정수형 텐서
# 두 번째 입력: fp32 
dummy_input_2 = torch.randn(1, 128, dtype=torch.float32)  # 두 번째 입력, 부동소수점 텐서

# 모델을 onnx 파일로 저장
torch.onnx.export(model, 
                  (dummy_input_1, dummy_input_2),  # 두 개의 입력을 튜플로 묶음
                  "mobilebert.onnx",
                  input_names=['input_1', 'input_2'],  # ONNX 모델에 입력 이름 지정
                  output_names=['output'],             # 출력 이름 지정
                  opset_version=11)

# 모델의 state_dict를 'mobilebert_model.ckpt' 파일로 저장
# PyTorch에서는 모델 가중치를 저장할 때 확장자 이름은 특별한 의미가 없으며, 
# 사용자의 선호에 따라 파일 확장자를 .pt, .pth, .ckpt 등으로 자유롭게 설정할 수 있다.
torch.save(model.state_dict(), "mobilebert_model.ckpt")

# 모델의 가중치뿐만 아니라 모델의 구조 전체를 저장하고 싶다면, torch.save로 모델 자체를 저장
# 모델 자체를 'mobilebert_complete_model.pt' 파일로 저장 (구조 + 가중치 포함)
torch.save(model, "mobilebert_complete_model.pt")
```

## 2. Aimet-model-zoo 추출

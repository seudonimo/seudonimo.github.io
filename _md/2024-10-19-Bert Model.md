---
title: Bert Model
author: seudonimo
date: 2024-10.19 00:34:00 +0800
categories: [Blogging, Note]
tags: [Bert, DL, Deep Learning]
---

Bert Model Download from HuggingFace

# BERT
## Bidirectional Encoder Representations from Transformers
- BERT는 다양한 자연어 처리 분야에서 좋은 성능을 내면서 여라가지 일들을 수행하는데 사용된다.

### 전이학습 모델
- 사전 학습된 대용량의 레이블링 되지 않은 데이터를 이용해서, 언어 모델(Language)을 학습하고 
- 이를 토대로 특정작업(문서 분류, QnA, 번역)을 위한 신경망을 추가하는 전이학습 방법이다.

### 사전학습 모델
- 대용량의 데어트를 직접 학습시키기 위해서는 매우 많은 자원과 시간이 필요하지만, 
- BERT 모델은 기본적으로 대량의 단어 임베딩 등에 대해 사전학습이 되어 있는 모델을 제공한다. 
- 그러므로 상대적으로 적은 자원만으로도 충분히 자연어 처리의 여러 일을 수행할 수 있다.

- 이전에는 단어 임베딩을 위해 Word2Vec, Glove, Fasttext 방식 등을 사용했지만, 
- BERT가 자연어 처리 분야의 11개 테스트에서 가장 좋은 성능을 차지했다.(2018년 기준)


## BERT Structure
![Input Representations](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpZneZ%2FbtqGg6mCUaU%2FEcXXk5nCUAdTRMK2vXORO0%2Fimg.png "Input Representation"){: width="100" height="100"}

- BERT의 Input Representation은 위 그림과 같이 세가지
## 미세 조정 시나리오

![Microsoft 서비스와 함께하는 미세 조정](../../../../translated_images/FinetuningwithMS.921fa8c240611562e7c4a5ceb7eca04f458ad6f3c899d5a0dc120030398d9e08.ko.png)

**플랫폼** 여기에는 Azure AI Studio, Azure Machine Learning, AI Tools, Kaito, ONNX Runtime 등 다양한 기술이 포함됩니다.

**인프라** 여기에는 미세 조정 과정에서 필수적인 CPU와 FPGA가 포함됩니다. 각 기술의 아이콘을 보여드리겠습니다.

**도구 및 프레임워크** 여기에는 ONNX Runtime과 ONNX Runtime이 포함됩니다. 각 기술의 아이콘을 보여드리겠습니다.
[ONNX Runtime과 ONNX Runtime의 아이콘 삽입]

Microsoft 기술을 활용한 미세 조정 과정은 다양한 구성 요소와 도구를 포함합니다. 이러한 기술을 이해하고 활용함으로써 애플리케이션을 효과적으로 미세 조정하고 더 나은 솔루션을 만들 수 있습니다.

## 서비스로서의 모델

호스팅된 미세 조정을 사용하여 컴퓨팅을 생성하고 관리할 필요 없이 모델을 미세 조정합니다.

![MaaS 미세 조정](../../../../translated_images/MaaSfinetune.1678f33544c36b9016d8c018ce9c4c1622fb3bc2d72751291c39813f88bce052.ko.png)

서버리스 미세 조정은 Phi-3-mini 및 Phi-3-medium 모델에 대해 제공되며, 개발자는 컴퓨팅을 준비할 필요 없이 클라우드 및 엣지 시나리오에 맞게 모델을 신속하고 쉽게 커스터마이징할 수 있습니다. 또한, Phi-3-small 모델이 이제 모델-서비스로 제공됨에 따라 개발자는 기본 인프라를 관리할 필요 없이 AI 개발을 신속하고 쉽게 시작할 수 있습니다.

[미세 조정 샘플](https://github.com/microsoft/Phi-3CookBook/blob/main/md/04.Fine-tuning/FineTuning_AIStudio.md)
## 플랫폼으로서의 모델

사용자가 자신의 컴퓨팅을 관리하여 모델을 미세 조정합니다.

![Maap 미세 조정](../../../../translated_images/MaaPFinetune.f88828d32d16ced1198525fceed9184ce17516f5c1a404c264d87a4ca816947f.ko.png)

[미세 조정 샘플](https://github.com/Azure/azureml-examples/blob/main/sdk/python/foundation-models/system/finetune/chat-completion/chat-completion.ipynb)

## 미세 조정 시나리오

| | | | | | | |
|-|-|-|-|-|-|-|
|시나리오|LoRA|QLoRA|PEFT|DeepSpeed|ZeRO|DORA|
|사전 학습된 LLM을 특정 작업이나 도메인에 맞게 적응|Yes|Yes|Yes|Yes|Yes|Yes|
|텍스트 분류, 명명된 개체 인식, 기계 번역과 같은 NLP 작업을 위한 미세 조정|Yes|Yes|Yes|Yes|Yes|Yes|
|QA 작업을 위한 미세 조정|Yes|Yes|Yes|Yes|Yes|Yes|
|챗봇에서 인간과 같은 응답을 생성하기 위한 미세 조정|Yes|Yes|Yes|Yes|Yes|Yes|
|음악, 예술 또는 기타 창의적 형태의 창작을 위한 미세 조정|Yes|Yes|Yes|Yes|Yes|Yes|
|계산 및 재정 비용 절감|Yes|Yes|No|Yes|Yes|No|
|메모리 사용량 절감|No|Yes|No|Yes|Yes|Yes|
|효율적인 미세 조정을 위한 더 적은 매개변수 사용|No|Yes|Yes|No|No|Yes|
|모든 GPU 장치의 총 GPU 메모리에 접근할 수 있는 메모리 효율적인 데이터 병렬 처리 형태|No|No|No|Yes|Yes|Yes|

## 미세 조정 성능 예시

![미세 조정 성능](../../../../translated_images/Finetuningexamples.88bad3a5350927b08b1f06e4bced95cfd3715caa933d21c9ff658dcf0db94f73.ko.png)

면책 조항: 이 번역은 원본을 AI 모델에 의해 번역된 것이며 완벽하지 않을 수 있습니다. 
출력을 검토하고 필요한 수정 사항을 반영해 주시기 바랍니다.
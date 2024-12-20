# **Nvidia Jetson에서 Phi-3 추론**

Nvidia Jetson은 Nvidia에서 제공하는 임베디드 컴퓨팅 보드 시리즈입니다. Jetson TK1, TX1, TX2 모델 모두 ARM 아키텍처 중앙 처리 장치(CPU)를 통합한 Nvidia의 Tegra 프로세서(또는 SoC)를 탑재하고 있습니다. Jetson은 저전력 시스템으로, 머신러닝 애플리케이션 가속화를 위해 설계되었습니다. Nvidia Jetson은 모든 산업에서 획기적인 AI 제품을 개발하는 전문 개발자들과, 실습을 통해 AI를 배우고 놀라운 프로젝트를 만드는 학생 및 열성 팬들이 사용합니다. SLM은 Jetson과 같은 엣지 디바이스에 배포되어 산업용 생성 AI 애플리케이션 시나리오의 구현을 더욱 향상시킬 수 있습니다.

## NVIDIA Jetson에서의 배포:
자율 로봇 및 임베디드 디바이스를 작업하는 개발자들은 Phi-3 Mini를 활용할 수 있습니다. Phi-3의 상대적으로 작은 크기는 엣지 배포에 이상적입니다. 매개변수는 훈련 중에 신중하게 조정되어 높은 응답 정확도를 보장합니다.

### TensorRT-LLM 최적화:
NVIDIA의 [TensorRT-LLM 라이브러리](https://github.com/NVIDIA/TensorRT-LLM?WT.mc_id=aiml-138114-kinfeylo)는 대형 언어 모델 추론을 최적화합니다. Phi-3 Mini의 긴 컨텍스트 윈도우를 지원하여 처리량과 지연 시간을 모두 향상시킵니다. 최적화에는 LongRoPE, FP8, inflight batching과 같은 기술이 포함됩니다.

### 가용성과 배포:
개발자들은 [NVIDIA의 AI](https://www.nvidia.com/en-us/ai-data-science/generative-ai/)에서 128K 컨텍스트 윈도우가 포함된 Phi-3 Mini를 탐색할 수 있습니다. 이는 표준 API를 갖춘 마이크로서비스인 NVIDIA NIM으로 패키징되어 어디서나 배포할 수 있습니다. 추가적으로, [GitHub의 TensorRT-LLM 구현](https://github.com/NVIDIA/TensorRT-LLM)도 확인할 수 있습니다.

 ## **1. 준비**

a. Jetson Orin NX / Jetson NX

b. JetPack 5.1.2+
   
c. Cuda 11.8
   
d. Python 3.8+

 ## **2. Jetson에서 Phi-3 실행하기**

 우리는 [Ollama](https://ollama.com) 또는 [LlamaEdge](https://llamaedge.com)를 선택할 수 있습니다.

 클라우드와 엣지 디바이스에서 동시에 gguf를 사용하고 싶다면, LlamaEdge는 WasmEdge로 이해할 수 있습니다 (WasmEdge는 클라우드 네이티브, 엣지 및 분산 애플리케이션에 적합한 경량, 고성능, 확장 가능한 WebAssembly 런타임입니다. 서버리스 애플리케이션, 임베디드 함수, 마이크로서비스, 스마트 계약 및 IoT 디바이스를 지원합니다. LlamaEdge를 통해 gguf의 정량화 모델을 엣지 디바이스와 클라우드에 배포할 수 있습니다).

![llamaedge](../../../../translated_images/llamaedge.d1314f30755868575f55e27125fdd9838b6962e3bce66c9bd21eaffebfcf57b9.ko.jpg)

다음은 사용하는 단계입니다:

1. 관련 라이브러리 및 파일 설치 및 다운로드

```bash

curl -sSf https://raw.githubusercontent.com/WasmEdge/WasmEdge/master/utils/install.sh | bash -s -- --plugin wasi_nn-ggml

curl -LO https://github.com/LlamaEdge/LlamaEdge/releases/latest/download/llama-api-server.wasm

curl -LO https://github.com/LlamaEdge/chatbot-ui/releases/latest/download/chatbot-ui.tar.gz

tar xzf chatbot-ui.tar.gz

```

**참고**: llama-api-server.wasm과 chatbot-ui는 동일한 디렉토리에 있어야 합니다.

2. 터미널에서 스크립트 실행

```bash

wasmedge --dir .:. --nn-preload default:GGML:AUTO:{Your gguf path} llama-api-server.wasm -p phi-3-chat

```

다음은 실행 결과입니다.

![llamaedgerun](../../../../translated_images/llamaedgerun.fcb0c81257035c00b2a9ec7d2f541d64f9f357eec4adf45f5c951c4c06cd1df9.ko.png)

***샘플 코드*** [Phi-3 mini WASM Notebook Sample](https://github.com/Azure-Samples/Phi-3MiniSamples/tree/main/wasm)

요약하자면, Phi-3 Mini는 효율성, 컨텍스트 인식, NVIDIA의 최적화 역량을 결합한 언어 모델링의 도약을 나타냅니다. 로봇이나 엣지 애플리케이션을 구축하든, Phi-3 Mini는 주목할 만한 강력한 도구입니다.

**면책 조항**:
이 문서는 기계 기반 AI 번역 서비스를 사용하여 번역되었습니다. 정확성을 위해 노력하고 있지만, 자동 번역에는 오류나 부정확성이 있을 수 있습니다. 원본 문서의 원어를 권위 있는 출처로 간주해야 합니다. 중요한 정보의 경우, 전문 인간 번역을 권장합니다. 이 번역 사용으로 인한 오해나 잘못된 해석에 대해서는 책임을 지지 않습니다.
# **Inference Phi-3 in iOS**


Phi-3-mini is available in iOS, Android, and Edge Device deployments, allowing generative AI to be deployed in BYOD. The following example deploys Phi-3-mini based on iOS

 ## **1. Preparation**


a. macOS 14+

b. Xcode 15+
   
c. iOS SDK 17.x 
   
d. Install Python 3.10+ (Conda is recommended)
   
e. Install the Python library - python-flatbuffers

f. Install CMake


### **2. Compiling ONNX Runtime for iOS**

```bash

git clone https://github.com/microsoft/onnxruntime.git

cd onnxruntime

./build.sh --build_shared_lib --ios --skip_tests --parallel --build_dir ./build_ios --ios --apple_sysroot iphoneos --osx_arch arm64 --apple_deploy_target 17.4 --cmake_generator Xcode --config Release

```
 
***Notice*** 

  a. Before compiling, you must ensure that Xcode is configured correctly and set it on the terminal


```bash

sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer 

```
 
  b. ONNX Runtime needs to be compiled based on different platforms. For iOS, you can compile based on arm64 / x86_64
   
  c. It is recommended to directly use the latest iOS SDK for compilation. Of course, you can also lower the version to be compatible with past SDKs.


### **3. Compiling Generative AI with ONNX Runtime for iOS**


 ***Note:*** Because Generative AI with ONNX Runtime is in preview, please note the changes.


```bash

git clone https://github.com/microsoft/onnxruntime-genai

cd onnxruntime-genai

git checkout yguo/ios-build-genai


mkdir ort

cd ort

mkdir include

mkdir lib

cd ../


cp ../onnxruntime/include/onnxruntime/core/session/onnxruntime_c_api.h ort/include
cp ../onnxruntime/build_ios/Release/Release-iphoneos/libonnxruntime*.dylib* ort/lib

python3 build.py --parallel --build_dir ./build_ios_simulator --ios --ios_sysroot iphoneos --osx_arch arm64 --apple_deployment_target 17.4 --cmake_generator Xcode

```


### **4. Create an App application in Xcode**

I chose Objective-C as the App development method , because using Generative AI with ONNX Runtime C++ API, Objective-C is better compatible. Of course, you can also complete related calls through Swift bridging.


![xcode](../../imgs/03/iOS/xcode.png)


### **E. Copy the ONNX quantized INT4 model to the App application project**

We need to import the INT4 quantization model in ONNX format, which needs to be downloaded first

![hf](../../imgs/03/iOS/hf.png)

After downloading, you need to add it to the Resources directory of the project in Xcode.


![model](../../imgs/03/iOS/model.png)


 ### **5. Add the C++ API in ViewControllers**
 
***Notice***:

  a. Add the corresponding C++ header file to the project


  ![head](../../imgs/03/iOS/head.png)

  b. add onnxruntime-gen ai dylib in Xcode

  
  ![lib](../../imgs/03/iOS/lib.png)
 
  c. Directly use the code on C Samples for testing in this samples. You can also directly add moreto run(such as ChatUI）

  d. Because you need to call C++, please change ViewController.m to ViewController.mm

```objc

    NSString *llmPath = [[NSBundle mainBundle] resourcePath];
    char const *modelPath = llmPath.cString;

    auto model =  OgaModel::Create(modelPath);

    auto tokenizer = OgaTokenizer::Create(*model);

    const char* prompt = "<|system|>You are a helpful AI assistant.<|end|><|user|>Can you introduce yourself?<|end|><|assistant|>";

    auto sequences = OgaSequences::Create();
    tokenizer->Encode(prompt, *sequences);

    auto params = OgaGeneratorParams::Create(*model);
    params->SetSearchOption("max_length", 100);
    params->SetInputSequences(*sequences);

    auto output_sequences = model->Generate(*params);
    const auto output_sequence_length = output_sequences->SequenceCount(0);
    const auto* output_sequence_data = output_sequences->SequenceData(0);
    auto out_string = tokenizer->Decode(output_sequence_data, output_sequence_length);
    
    auto tmp = out_string;

```


### **6. Look at the running results**

![result](../../imgs/03/iOS/result.jpg)

***Sample Codes：*** https://github.com/Azure-Samples/Phi-3MiniSamples/tree/main/ios
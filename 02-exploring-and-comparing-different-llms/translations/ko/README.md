# 다양한 LLM 탐색 및 비교

[![다양한 LLM 탐색 및 비교](../../images/02-lesson-banner.png?WT.mc_id=academic-105485-koreyst)](https://aka.ms/gen-ai-lesson2-gh?WT.mc_id=academic-105485-koreyst)

> _위 이미지를 클릭하면 이 수업의 영상을 볼 수 있습니다_

이전 수업에서 우리는 생성형 AI가 기술 환경을 어떻게 변화시키고 있는지, 대규모 언어 모델(LLM)이 어떻게 작동하는지, 그리고 우리 스타트업과 같은 기업이 어떻게 이를 활용하여 성장할 수 있는지 살펴보았습니다. 이번 장에서는 다양한 유형의 대규모 언어 모델(LLM)을 비교하고 대조하여 각각의 장단점을 이해해 보겠습니다.

우리 스타트업 여정의 다음 단계는 현재 LLM 환경을 탐색하고 우리의 사용 사례에 적합한 모델을 이해하는 것입니다.

## 소개

이 수업에서는 다음 내용을 다룰 것입니다:

- 현재 환경에서의 다양한 LLM 유형
- Azure에서 사용 사례에 맞는 다양한 모델 테스트, 반복, 비교
- LLM 배포 방법

## 학습 목표

이 수업을 마치면 다음을 할 수 있게 됩니다:

- 사용 사례에 맞는 적절한 모델 선택
- 모델의 테스트, 반복, 성능 개선 방법 이해
- 기업이 모델을 배포하는 방법 파악

## 다양한 LLM 유형 이해하기

LLM은 그 구조, 훈련 데이터, 사용 사례에 따라 여러 가지로 분류될 수 있습니다. 이러한 차이점을 이해하면 우리 스타트업이 시나리오에 맞는 적절한 모델을 선택하고, 테스트, 반복, 성능 개선 방법을 이해하는 데 도움이 될 것입니다.

LLM 모델에는 여러 유형이 있으며, 모델 선택은 사용 목적, 데이터, 지불 가능한 비용 등 여러 요소에 따라 달라집니다.

텍스트, 오디오, 비디오, 이미지 생성 등 어떤 용도로 모델을 사용할 것인지에 따라 다른 유형의 모델을 선택할 수 있습니다.

- **오디오 및 음성 인식**. 이 목적으로는 Whisper 유형 모델이 좋은 선택입니다. 이는 범용 모델로 음성 인식에 특화되어 있습니다. 다양한 오디오로 훈련되어 다국어 음성 인식이 가능합니다. [Whisper 유형 모델에 대해 자세히 알아보세요](https://platform.openai.com/docs/models/whisper?WT.mc_id=academic-105485-koreyst).

- **이미지 생성**. 이미지 생성을 위해서는 DALL-E와 Midjourney가 잘 알려진 선택지입니다. DALL-E는 Azure OpenAI에서 제공됩니다. [DALL-E에 대해 여기에서 더 읽어보세요](https://platform.openai.com/docs/models/dall-e?WT.mc_id=academic-105485-koreyst). 이 커리큘럼의 9장에서도 다룹니다.

- **텍스트 생성**. 대부분의 모델은 텍스트 생성에 대해 훈련되어 있으며, GPT-3.5부터 GPT-4까지 다양한 선택지가 있습니다. GPT-4가 가장 비싸며 각각 다른 비용이 듭니다. [Azure OpenAI 플레이그라운드](https://oai.azure.com/portal/playground?WT.mc_id=academic-105485-koreyst)를 살펴보고 능력과 비용 면에서 어떤 모델이 가장 적합한지 평가해 보는 것이 좋습니다.

- **멀티모달리티**. 입력과 출력에서 여러 유형의 데이터를 처리하고자 한다면, [gpt-4 turbo with vision이나 gpt-4o](https://learn.microsoft.com/azure/ai-services/openai/concepts/models#gpt-4-and-gpt-4-turbo-models?WT.mc_id=academic-105485-koreyst) 같은 모델을 고려해 볼 수 있습니다. 이는 OpenAI 모델의 최신 버전으로, 자연어 처리와 시각적 이해를 결합하여 멀티모달 인터페이스를 통한 상호작용이 가능합니다.

모델을 선택하면 기본적인 능력을 얻게 되지만, 이것만으로는 충분하지 않을 수 있습니다. 종종 회사 특정 데이터를 LLM에 알려줘야 할 필요가 있습니다. 이를 접근하는 방법에는 몇 가지가 있으며, 이에 대해서는 다음 섹션에서 더 자세히 다룰 것입니다.

### 기초 모델과 LLM의 차이

기초 모델이라는 용어는 [스탠포드 연구자들이 만들었으며](https://arxiv.org/abs/2108.07258?WT.mc_id=academic-105485-koreyst), 다음과 같은 기준을 따르는 AI 모델로 정의됩니다:

- **비지도 학습 또는 자기 지도 학습을 통해 훈련됩니다**. 즉, 레이블이 없는 다중 모달 데이터로 훈련되며, 훈련 과정에서 인간의 주석이나 데이터 레이블링이 필요하지 않습니다.

- **매우 큰 모델입니다**. 수십억 개의 매개변수로 훈련된 매우 깊은 신경망을 기반으로 합니다.

- **일반적으로 다른 모델의 '기초'로 사용됩니다**. 즉, 다른 모델의 출발점으로 사용될 수 있으며, 이는 미세 조정을 통해 이루어질 수 있습니다.

![기초 모델과 LLM의 차이](../../images/FoundationModel.png?WT.mc_id=academic-105485-koreyst)

이미지 출처: [Essential Guide to Foundation Models and Large Language Models | by Babar M Bhatti | Medium](https://thebabar.medium.com/essential-guide-to-foundation-models-and-large-language-models-27dab58f7404)

이 구분을 더 명확히 하기 위해 ChatGPT를 예로 들어보겠습니다. ChatGPT의 첫 버전을 만들 때, GPT-3.5라는 모델이 기초 모델 역할을 했습니다. 이는 OpenAI가 채팅 특화 데이터를 사용하여 GPT-3.5의 조정된 버전을 만들어 챗봇과 같은 대화 시나리오에서 잘 작동하도록 특화시켰다는 것을 의미합니다.

![기초 모델](../../images/Multimodal.png?WT.mc_id=academic-105485-koreyst)

이미지 출처: [2108.07258.pdf (arxiv.org)](https://arxiv.org/pdf/2108.07258.pdf?WT.mc_id=academic-105485-koreyst)

### 오픈 소스 모델과 독점 모델

LLM을 분류하는 또 다른 방법은 오픈 소스인지 독점 모델인지에 따른 것입니다.

오픈 소스 모델은 대중에게 공개되어 누구나 사용할 수 있는 모델입니다. 주로 모델을 만든 회사나 연구 커뮤니티에 의해 공개됩니다. 이러한 모델은 검사, 수정, 그리고 LLM의 다양한 사용 사례에 맞게 커스터마이징할 수 있습니다. 하지만 항상 프로덕션 사용에 최적화되어 있지는 않으며, 독점 모델만큼 성능이 좋지 않을 수 있습니다. 또한, 오픈 소스 모델에 대한 자금 지원이 제한적일 수 있어 장기적으로 유지보수되지 않거나 최신 연구로 업데이트되지 않을 수 있습니다. 인기 있는 오픈 소스 모델의 예로는 [Alpaca](https://crfm.stanford.edu/2023/03/13/alpaca.html?WT.mc_id=academic-105485-koreyst), [Bloom](https://huggingface.co/bigscience/bloom), [LLaMA](https://llama.meta.com) 등이 있습니다.

독점 모델은 회사가 소유하고 있으며 대중에게 공개되지 않는 모델입니다. 이러한 모델은 주로 프로덕션 사용에 최적화되어 있습니다. 하지만 검사, 수정, 또는 다른 사용 사례에 맞게 커스터마이징할 수 없습니다. 또한, 항상 무료로 사용할 수 있는 것은 아니며, 사용을 위해 구독이나 결제가 필요할 수 있습니다. 사용자는 모델 훈련에 사용된 데이터를 제어할 수 없기 때문에, 데이터 프라이버시와 AI의 책임 있는 사용을 보장하는 것은 모델 소유자를 신뢰해야 합니다. 인기 있는 독점 모델의 예로는 [OpenAI 모델](https://platform.openai.com/docs/models/overview?WT.mc_id=academic-105485-koreyst), [Google Bard](https://sapling.ai/llm/bard?WT.mc_id=academic-105485-koreyst), [Claude 2](https://www.anthropic.com/index/claude-2?WT.mc_id=academic-105485-koreyst) 등이 있습니다.

### 임베딩 vs 이미지 생성 vs 텍스트 및 코드 생성

LLM은 생성하는 출력에 따라서도 분류될 수 있습니다.

임베딩은 텍스트를 숫자 형태로 변환하는 모델 집합입니다. 이를 임베딩이라고 하며, 입력 텍스트의 수치적 표현입니다. 임베딩은 기계가 단어나 문장 간의 관계를 이해하기 쉽게 만들며, 분류 모델이나 숫자 데이터에 더 나은 성능을 보이는 클러스터링 모델과 같은 다른 모델의 입력으로 사용될 수 있습니다. 임베딩 모델은 종종 전이 학습에 사용되는데, 이는 풍부한 데이터가 있는 대리 작업을 위해 모델을 구축한 다음, 모델 가중치(임베딩)를 다른 하위 작업에 재사용하는 것입니다. 이 카테고리의 예로는 [OpenAI 임베딩](https://platform.openai.com/docs/models/embeddings?WT.mc_id=academic-105485-koreyst)이 있습니다.

![임베딩](../../images/Embedding.png?WT.mc_id=academic-105485-koreyst)

이미지 생성 모델은 이미지를 생성하는 모델입니다. 이러한 모델은 주로 이미지 편집, 이미지 합성, 이미지 번역에 사용됩니다. 이미지 생성 모델은 주로 [LAION-5B](https://laion.ai/blog/laion-5b/?WT.mc_id=academic-105485-koreyst)와 같은 대규모 이미지 데이터셋으로 훈련되며, 새로운 이미지를 생성하거나 인페인팅, 초해상도, 색상화 기술을 사용하여 기존 이미지를 편집하는 데 사용될 수 있습니다. 예로는 [DALL-E-3](https://openai.com/dall-e-3?WT.mc_id=academic-105485-koreyst)와 [Stable Diffusion 모델](https://github.com/Stability-AI/StableDiffusion?WT.mc_id=academic-105485-koreyst)이 있습니다.

![이미지 생성](../../images/Image.png?WT.mc_id=academic-105485-koreyst)

텍스트 및 코드 생성 모델은 텍스트나 코드를 생성하는 모델입니다. 이러한 모델은 주로 텍스트 요약, 번역, 질문 답변에 사용됩니다. 텍스트 생성 모델은 주로 [BookCorpus](https://www.cv-foundation.org/openaccess/content_iccv_2015/html/Zhu_Aligning_Books_and_ICCV_2015_paper.html?WT.mc_id=academic-105485-koreyst)와 같은 대규모 텍스트 데이터셋으로 훈련되며, 새로운 텍스트를 생성하거나 질문에 답변하는 데 사용될 수 있습니다. [CodeParrot](https://huggingface.co/codeparrot?WT.mc_id=academic-105485-koreyst)과 같은 코드 생성 모델은 주로 GitHub와 같은 대규모 코드 데이터셋으로 훈련되며, 새로운 코드를 생성하거나 기존 코드의 버그를 수정하는 데 사용될 수 있습니다.

![텍스트 및 코드 생성](../../images/Text.png?WT.mc_id=academic-105485-koreyst)

### 인코더-디코더 vs 디코더 전용

LLM의 다양한 아키텍처 유형을 설명하기 위해 비유를 들어보겠습니다.

여러분의 상사가 학생들을 위한 퀴즈를 만드는 과제를 줬다고 상상해 보세요. 두 명의 동료가 있는데, 한 명은 내용 만들기를 담당하고 다른 한 명은 검토를 담당합니다.

내용 만드는 사람은 디코더 전용 모델과 비슷합니다. 주제를 보고 여러분이 이미 쓴 내용을 확인한 다음, 그걸 바탕으로 강의를 만들 수 있죠. 흥미롭고 유익한 내용을 쓰는 데는 아주 뛰어나지만, 주제와 학습 목표를 이해하는 데는 그리 좋지 않습니다. GPT-3 같은 GPT 계열 모델들이 디코더 모델의 예시입니다.

검토하는 사람은 인코더 전용 모델과 비슷합니다. 작성된 강의와 답변을 보고 그들 사이의 관계를 파악하고 맥락을 이해하지만, 내용을 만들어내는 데는 약합니다. BERT가 인코더 전용 모델의 예시입니다.

퀴즈를 만들고 검토할 수 있는 사람이 있다고 상상해 보세요. 이게 바로 인코더-디코더 모델입니다. BART와 T5가 그 예시죠.

### 서비스 vs 모델

이제 서비스와 모델의 차이에 대해 얘기해 봅시다. 서비스는 클라우드 서비스 제공업체가 제공하는 제품으로, 보통 모델, 데이터, 기타 구성 요소의 조합입니다. 모델은 서비스의 핵심 구성 요소로, 주로 LLM과 같은 기초 모델입니다.

서비스는 보통 실제 사용 환경에 최적화되어 있고, 그래픽 사용자 인터페이스를 통해 모델보다 사용하기 쉽습니다. 하지만 서비스는 항상 무료인 것은 아니며, 사용하려면 구독이나 결제가 필요할 수 있습니다. 대신 서비스 제공자의 장비와 자원을 활용하여 비용을 최적화하고 쉽게 확장할 수 있죠. [Azure OpenAI 서비스](https://learn.microsoft.com/azure/ai-services/openai/overview?WT.mc_id=academic-105485-koreyst)가 그 예시입니다. 이 서비스는 사용한 만큼 지불하는 요금제를 제공하여 사용량에 비례해 요금을 부과합니다. 또한 Azure OpenAI 서비스는 모델의 기능 위에 기업급 보안과 책임 있는 AI 프레임워크를 제공합니다.

모델은 단순히 매개변수, 가중치 등을 가진 신경망입니다. 기업이 로컬에서 실행할 수 있게 해주지만, 장비를 구매하고 확장을 위한 구조를 구축하며 라이선스를 구매하거나 오픈 소스 모델을 사용해야 합니다. LLaMA 같은 모델은 사용할 수 있지만, 모델을 실행하려면 컴퓨팅 파워가 필요합니다.

## Azure에서 다양한 모델의 성능을 이해하기 위한 테스트 및 반복 방법

우리 팀이 현재 LLM 환경을 탐색하고 시나리오에 적합한 후보들을 식별했다면, 다음 단계는 자체 데이터와 워크로드에서 이들을 테스트하는 것입니다. 이는 실험과 측정을 통한 반복적인 과정입니다.

앞서 언급한 대부분의 모델(OpenAI 모델, Llama2와 같은 오픈 소스 모델, Hugging Face 트랜스포머)은 [Azure AI Studio](https://ai.azure.com/?WT.mc_id=academic-105485-koreyst)의 [모델 카탈로그](https://learn.microsoft.com/azure/ai-studio/how-to/model-catalog-overview?WT.mc_id=academic-105485-koreyst)에서 사용할 수 있습니다.

[Azure AI Studio](https://learn.microsoft.com/azure/ai-studio/what-is-ai-studio?WT.mc_id=academic-105485-koreyst)는 개발자가 생성형 AI 애플리케이션을 구축하고 전체 개발 수명 주기를 관리할 수 있도록 설계된 클라우드 플랫폼입니다. 실험부터 평가까지 모든 Azure AI 서비스를 단일 허브로 통합하며 편리한 GUI를 제공합니다. Azure AI Studio의 모델 카탈로그를 통해 사용자는 다음과 같은 작업을 수행할 수 있습니다:

- 카탈로그에서 관심 있는 기초 모델을 찾습니다 - 독점 또는 오픈 소스 모델을 작업, 라이선스 또는 이름으로 필터링할 수 있습니다. 검색 편의성을 높이기 위해 모델은 Azure OpenAI 컬렉션, Hugging Face 컬렉션 등의 컬렉션으로 구성되어 있습니다.

![모델 카탈로그](../../images/AzureAIStudioModelCatalog.png?WT.mc_id=academic-105485-koreyst)

- 모델 카드를 검토합니다. 여기에는 의도된 사용 및 훈련 데이터에 대한 자세한 설명, 코드 샘플, 내부 평가 라이브러리의 평가 결과가 포함됩니다.

![모델 카드](../../images/ModelCard.png?WT.mc_id=academic-105485-koreyst)

- [모델 벤치마크](https://learn.microsoft.com/azure/ai-studio/how-to/model-benchmarks?WT.mc_id=academic-105485-koreyst) 창을 통해 업계에서 사용 가능한 모델과 데이터셋 간의 벤치마크를 비교하여 비즈니스 시나리오에 가장 적합한 모델을 평가합니다.

![모델 벤치마크](../../images/ModelBenchmarks.png?WT.mc_id=academic-105485-koreyst)

- Azure AI Studio의 실험 및 추적 기능을 활용하여 특정 워크로드에서 모델 성능을 향상시키기 위해 사용자 정의 훈련 데이터로 모델을 미세 조정합니다.

![모델 미세 조정](../../images/FineTuning.png?WT.mc_id=academic-105485-koreyst)

- 원본 사전 훈련 모델 또는 미세 조정된 버전을 원격 실시간 추론(관리형 컴퓨팅) 또는 서버리스 API 엔드포인트([사용량 기반 과금](https://learn.microsoft.com/azure/ai-studio/how-to/model-catalog-overview#model-deployment-managed-compute-and-serverless-api-pay-as-you-go?WT.mc_id=academic-105485-koreyst))에 배포하여 애플리케이션에서 사용할 수 있게 합니다.

![모델 배포](../../images/ModelDeploy.png?WT.mc_id=academic-105485-koreyst)

> [!참고]
> 현재 카탈로그의 모든 모델이 미세 조정 및/또는 사용량 기반 과금 배포에 사용 가능한 것은 아닙니다. 모델의 기능과 제한 사항에 대한 자세한 내용은 모델 카드를 확인하세요.

## LLM 결과 개선하기

우리 스타트업 팀과 함께 다양한 종류의 LLM과 클라우드 플랫폼(Azure Machine Learning)을 탐색했습니다. 이를 통해 다양한 모델을 비교하고, 테스트 데이터로 평가하며, 성능을 개선하고, 추론 엔드포인트에 배포할 수 있게 되었습니다.

그렇다면 사전 훈련된 모델을 사용하는 대신 모델을 미세 조정해야 하는 경우는 언제일까요? 특정 워크로드에서 모델 성능을 향상시키는 다른 접근 방식은 없을까요?

기업이 LLM에서 필요한 결과를 얻기 위해 사용할 수 있는 여러 접근 방식이 있습니다. 프로덕션에 LLM을 배포할 때 다양한 수준의 복잡성, 비용, 품질을 가진 다양한 유형의 모델과 훈련 정도를 선택할 수 있습니다. 다음은 몇 가지 다른 접근 방식입니다:

- **컨텍스트를 포함한 프롬프트 엔지니어링**. 필요한 응답을 얻기 위해 프롬프트에 충분한 컨텍스트를 제공하는 것입니다.

- **검색 증강 생성(RAG)**. 데이터가 데이터베이스나 웹 엔드포인트에 있을 수 있습니다. 이 데이터 또는 그 일부를 프롬프트 시점에 포함시키기 위해 관련 데이터를 가져와 사용자의 프롬프트의 일부로 만들 수 있습니다.

- **미세 조정된 모델**. 여기서는 자체 데이터로 모델을 추가 훈련시켜 모델이 더 정확하고 요구 사항에 더 잘 반응하도록 만듭니다. 하지만 비용이 많이 들 수 있습니다.

![LLM 배포](../../images/Deploy.png?WT.mc_id=academic-105485-koreyst)

이미지 출처: [기업이 LLM을 배포하는 네 가지 방법 | Fiddler AI 블로그](https://www.fiddler.ai/blog/four-ways-that-enterprises-deploy-llms?WT.mc_id=academic-105485-koreyst)

### 컨텍스트를 포함한 프롬프트 엔지니어링

사전 훈련된 LLM은 일반화된 자연어 작업에서 매우 잘 작동합니다. 심지어 완성할 문장이나 질문과 같은 짧은 프롬프트만으로도 - 이른바 "제로샷" 학습으로 - 좋은 결과를 얻을 수 있습니다.

하지만 사용자가 상세한 요청과 예시를 포함한 컨텍스트로 질의를 구체화할수록, 답변은 더 정확하고 사용자의 기대에 가까워집니다. 이 경우, 프롬프트에 하나의 예시만 포함되면 "원샷" 학습, 여러 예시가 포함되면 "퓨샷 학습"이라고 합니다.

컨텍스트를 포함한 프롬프트 엔지니어링은 시작하기에 가장 비용 효율적인 접근 방식입니다.

### 검색 증강 생성(RAG)

LLM은 답변을 생성할 때 훈련 과정에서 사용된 데이터만 활용할 수 있다는 한계가 있습니다. 이는 훈련 과정 이후에 발생한 사실들에 대해 알지 못하며, 비공개 정보(예: 회사 데이터)에 접근할 수 없다는 것을 의미합니다.

이는 RAG를 통해 극복할 수 있습니다. RAG는 프롬프트 길이 제한을 고려하여 외부 데이터를 문서 조각 형태로 프롬프트에 추가하는 기술입니다. 이는 [Azure Vector Search](https://learn.microsoft.com/azure/search/vector-search-overview?WT.mc_id=academic-105485-koreyst)와 같은 벡터 데이터베이스 도구를 통해 지원되며, 이 도구는 다양한 사전 정의된 데이터 소스에서 유용한 조각들을 검색하여 프롬프트 컨텍스트에 추가합니다.

이 기술은 기업이 LLM을 미세 조정할 만큼의 충분한 데이터, 시간 또는 자원이 없지만, 여전히 특정 워크로드에서의 성능을 향상시키고 현실 왜곡이나 유해 콘텐츠와 같은 위험을 줄이고자 할 때 매우 유용합니다.

### 미세 조정된 모델

미세 조정은 전이 학습을 활용하여 모델을 하위 작업에 '적응'시키거나 특정 문제를 해결하도록 하는 과정입니다. 퓨샷 학습과 RAG와는 달리, 이는 가중치와 편향이 업데이트된 새로운 모델을 생성합니다. 단일 입력(프롬프트)과 그에 연관된 출력(완성)으로 구성된 훈련 예제 세트가 필요합니다.

다음과 같은 경우에 이 접근 방식이 선호됩니다:

- **미세 조정된 모델 사용**. 기업이 고성능 모델 대신 미세 조정된 덜 능력 있는 모델(예: 임베딩 모델)을 사용하고자 할 때, 이는 더 비용 효율적이고 빠른 솔루션을 제공합니다.

- **지연 시간 고려**. 특정 사용 사례에서 지연 시간이 중요하여 매우 긴 프롬프트를 사용할 수 없거나, 모델이 학습해야 할 예제 수가 프롬프트 길이 제한에 맞지 않을 때 유용합니다.

- **최신 상태 유지**. 기업이 많은 고품질 데이터와 정답 레이블을 보유하고 있으며, 이 데이터를 시간이 지나도 최신 상태로 유지할 수 있는 자원이 있을 때 적합합니다.

### 훈련된 모델

LLM을 처음부터 훈련시키는 것은 의심할 여지 없이 가장 어렵고 복잡한 접근 방식입니다. 이는 막대한 양의 데이터, 숙련된 인력, 적절한 컴퓨팅 파워를 필요로 합니다. 이 옵션은 기업이 도메인 특화 사용 사례와 대량의 도메인 중심 데이터를 보유한 시나리오에서만 고려해야 합니다.

## 복습

LLM 완성 결과를 개선하기 위한 좋은 접근 방식은 무엇일까요?

1. 컨텍스트를 포함한 프롬프트 엔지니어링
2. RAG
3. 미세 조정된 모델

A: 3번입니다. 시간과 자원, 그리고 고품질 데이터가 있다면 최신 상태를 유지하기 위해 미세 조정이 더 나은 옵션입니다. 하지만 시간이 부족한 상황에서 개선을 원한다면 먼저 RAG를 고려해 볼 만합니다.

## 🚀 도전 과제

비즈니스에 [RAG를 사용하는 방법](https://learn.microsoft.com/azure/search/retrieval-augmented-generation-overview?WT.mc_id=academic-105485-koreyst)에 대해 더 자세히 알아보세요.

## 잘 하셨습니다. 학습을 계속하세요

이 수업을 마친 후, [생성형 AI 학습 컬렉션](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst)을 확인하여 생성형 AI 지식을 계속 향상시켜 보세요!

3장으로 넘어가 [책임감 있게 생성형 AI 구축하기](../../../03-using-generative-ai-responsibly/translations/ko/README.md?WT.mc_id=academic-105485-koreyst)에 대해 알아보겠습니다!

# 이 코스 시작하기

여러분이 이 코스를 시작하고 생성형 AI로 무엇을 만들어낼지 매우 기대됩니다!

성공적인 학습을 위해 이 페이지에서는 설정 단계, 기술적 요구사항, 그리고 필요할 때 도움을 받을 수 있는 방법을 안내합니다.

## 설정 단계

이 코스를 시작하려면 다음 단계를 완료해야 합니다.

### 1. 레포지토리 포크하기

코드를 변경하고 과제를 완료할 수 있도록 [이 전체 레포지토리를 포크](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst)하여 자신의 GitHub 계정으로 가져오세요. 또한 [이 레포지토리에 별표(🌟)를 주면](https://docs.github.com/en/get-started/exploring-projects-on-github/saving-repositories-with-stars?WT.mc_id=academic-105485-koreyst) 이 레포지토리와 관련 레포지토리를 더 쉽게 찾을 수 있습니다.

### 2. 코드스페이스 만들기

코드 실행 시 종속성 문제를 피하기 위해 [GitHub Codespaces](https://github.com/features/codespaces?WT.mc_id=academic-105485-koreyst)에서 이 코스를 실행하는 것을 권장합니다.

코드스페이스는 포크한 레포지토리에서 `Code` 옵션을 선택한 다음 **Codespaces** 옵션을 선택하여 만들 수 있습니다.

![코드스페이스를 만들기 위한 버튼을 보여주는 대화 상자](../../images/who-will-pay.webp?WT.mc_id=academic-105485-koreyst)

### 3. API 키 저장하기

어떠한 종류의 어플리케이션을 개발하든지 API 키를 안전하게 보관하는 것은 중요합니다. 코드에 직접 API 키를 저장하지 않는 것을 권장하며, 공개 레포지토리에 이러한 정보를 커밋하면 보안 문제가 발생할 수 있으며, 악의적인 사용자에 의해 원치 않는 비용이 발생할 수 있습니다.

## 컴퓨터에서 로컬로 실행하는 방법

컴퓨터에서 코드를 로컬로 실행하려면 [Python이 설치](https://www.python.org/downloads/?WT.mc_id=academic-105485-koreyst)되어 있어야 합니다.

그런 다음 레포지토리를 사용하려면 다음과 같이 클론해야 합니다:

```shell
git clone https://github.com/microsoft/generative-ai-for-beginners
cd generative-ai-for-beginners
```

모든 것을 확인했다면 시작할 준비가 되었습니다.

### Miniconda 설치하기 (선택)

[Miniconda](https://conda.io/en/latest/miniconda.html?WT.mc_id=academic-105485-koreyst)는 [Conda](https://docs.conda.io/en/latest?WT.mc_id=academic-105485-koreyst), Python, 그리고 몇 가지 패키지를 설치하기 위한 경량 설치 프로그램입니다.

Conda 자체는 패키지 관리자로, 다양한 Python [**가상 환경**](https://docs.python.org/3/tutorial/venv.html?WT.mc_id=academic-105485-koreyst)과 패키지를 쉽게 설정하고 전환할 수 있게 해줍니다. 또한 `pip`로 설치할 수 없는 패키지를 설치할 때도 유용합니다.

[MiniConda 설치 가이드](https://docs.anaconda.com/free/miniconda/#quick-command-line-install?WT.mc_id=academic-105485-koreyst)를 따라 설정할 수 있습니다.

Miniconda를 설치한 후, [레포지토리](https://github.com/microsoft/generative-ai-for-beginners/fork?WT.mc_id=academic-105485-koreyst)를 클론해야 합니다 (아직 하지 않았다면).

다음으로, 가상 환경을 만들어야 합니다. Conda로 이를 수행하려면 새 환경 파일(_environment.yml_)을 만듭니다. Codespaces를 사용하고 있다면 `.devcontainer` 디렉토리 내에 `.devcontainer/environment.yml`로 만듭니다.

환경 파일에 아래 스니펫을 채워넣으세요:

```yml
name: <environment-name>
channels:
  - defaults
dependencies:
  - python=<python-version>
  - openai
  - python-dotenv

```

환경 파일은 필요한 종속성을 지정합니다. `<environment-name>`은 Conda 환경에 사용하고 싶은 이름을 의미하고, `<python-version>`은 사용하고 싶은 Python 버전입니다. 예를 들어, `3`은 최신 주 버전의 Python입니다.

이를 완료한 후, 명령줄/터미널에서 아래 명령을 실행하여 Conda 환경을 만들 수 있습니다:

```bash
conda env create --name ai4beg --file .devcontainer/environment.yml # .devcontainer sub path applies to only Codespace setups
conda activate ai4beg
```

문제가 발생하면 [conda 환경 가이드](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?WT.mc_id=academic-105485-koreyst)를 참조하세요.

### Python 확장 프로그램이 설치된 Visual Studio Code 사용하기

이 코스를 위해 [Python 확장 프로그램](https://marketplace.visualstudio.com/items?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst)이 설치된 [Visual Studio Code (VS Code)](http://code.visualstudio.com/?WT.mc_id=academic-105485-koreyst) 편집기를 사용하는 것을 권장합니다. 하지만 이는 권장 사항일 뿐이며 절대적인 요구 사항은 아닙니다.

> **참고**: VS Code에서 코스 레포지토리를 열면 컨테이너 내에서 프로젝트를 설정할 수 있는 옵션이 있습니다. 이는 코스 레포지토리 내에 있는 [특별한 `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python&WT.mc_id=academic-105485-koreyst) 디렉토리 때문인데요. 이에 대해서는 나중에 더 자세히 설명하겠습니다.

> **참고**: VS Code에서 디렉토리를 클론하고 열면 자동으로 Python 확장 프로그램 설치를 제안할 것입니다.

> **참고**: VS Code가 컨테이너에서 레포지토리를 다시 열 것을 제안하면, 로컬에 설치된 Python 버전을 사용하기 위해 이 요청을 거절하세요.

### 브라우저에서 Jupyter 사용하기

[Jupyter 환경](https://jupyter.org?WT.mc_id=academic-105485-koreyst)을 사용하여 브라우저에서 직접 프로젝트 작업을 할 수도 있습니다. 클래식 Jupyter와 [Jupyter Hub](https://jupyter.org/hub?WT.mc_id=academic-105485-koreyst) 모두 자동 완성, 코드 강조 등의 기능을 갖춘 매우 편리한 개발 환경을 제공합니다.

Jupyter를 로컬에서 시작하려면 터미널/명령줄로 이동하여 코스 디렉토리로 이동한 후 다음을 실행하세요:

```bash
jupyter notebook
```

또는

```bash
jupyterhub
```

이렇게 하면 Jupyter 인스턴스가 시작되고 명령줄 창에 접근할 수 있는 URL이 표시됩니다.

URL에 접속하면 코스 개요를 볼 수 있고 모든 `*.ipynb` 파일로 이동할 수 있습니다. 예를 들어, `08-building-search-applications/python/oai-solution.ipynb`와 같은 파일입니다.

### 컨테이너에서 실행하기

컴퓨터나 Codespace에 모든 것을 설정하는 대신 [컨테이너](https://en.wikipedia.org/wiki/Containerization_(computing)?WT.mc_id=academic-105485-koreyst)를 사용할 수 있습니다. 코스 레포지토리 내의 특별한 `.devcontainer` 폴더를 통해 VS Code가 컨테이너 내에서 프로젝트를 설정할 수 있습니다. Codespaces 외부에서는 Docker 설치가 필요하며, 솔직히 약간의 작업이 필요하므로 컨테이너 작업 경험이 있는 분들에게만 권장합니다.

GitHub Codespaces를 사용할 때 API 키를 안전하게 보관하는 가장 좋은 방법 중 하나는 Codespace Secrets를 사용하는 것입니다. 이에 대해 자세히 알아보려면 [Codespaces 비밀 관리](https://docs.github.com/en/codespaces/managing-your-codespaces/managing-secrets-for-your-codespaces?WT.mc_id=academic-105485-koreyst) 가이드를 참조하세요.

## 강의 및 기술 요구사항

이 코스는 6개의 개념 강의와 6개의 코딩 강의로 구성되어 있습니다.

코딩 강의에서는 Azure OpenAI 서비스를 사용합니다. 이 코드를 실행하려면 Azure OpenAI 서비스에 대한 접근 권한과 API 키가 필요합니다. [이 신청서를 작성](https://azure.microsoft.com/products/ai-services/openai-service?WT.mc_id=academic-105485-koreyst)하여 접근 권한을 얻을 수 있습니다.

신청서 처리를 기다리는 동안 각 코딩 강의에는 코드와 출력을 볼 수 있는 `README.md` 파일이 포함되어 있습니다.

## Azure OpenAI 서비스 처음 사용하기

Azure OpenAI 서비스를 처음 사용하는 경우, [Azure OpenAI 서비스 리소스를 생성하고 배포하는 방법](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal&WT.mc_id=academic-105485-koreyst)에 대한 가이드를 참조하세요.

## OpenAI API 처음 사용하기

OpenAI API를 처음 사용하는 경우, [인터페이스를 생성하고 사용하는 방법](https://platform.openai.com/docs/quickstart?context=pythont&WT.mc_id=academic-105485-koreyst)에 대한 가이드를 참조하세요.

## 다른 학습자 만나기

다른 학습자들을 만나기 위해 공식 [AI 커뮤니티 Discord 서버](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)에 채널을 만들었습니다. 이는 비슷한 생각을 가진 기업가, 개발자, 학생, 그리고 생성형 AI에서 실력을 향상시키고자 하는 모든 사람들과 네트워킹할 수 있는 좋은 방법입니다.

[![Discord 채널 참여하기](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://aka.ms/genai-discord?WT.mc_id=academic-105485-koreyst)

프로젝트 팀도 학습자들을 돕기 위해 이 Discord 서버에 있을 것입니다.

## 기여하기

이 코스는 오픈 소스 이니셔티브입니다. 개선이 필요한 부분이나 문제를 발견하면 [Pull Request](https://github.com/microsoft/generative-ai-for-beginners/pulls?WT.mc_id=academic-105485-koreyst)를 생성하거나 [GitHub 이슈](https://github.com/microsoft/generative-ai-for-beginners/issues?WT.mc_id=academic-105485-koreyst)를 등록해 주세요.

프로젝트 팀은 모든 기여를 추적할 겁니다. 오픈 소스에 기여하는 것은 생성형 AI 분야에서 경력을 쌓는 훌륭한 방법입니다.

대부분의 기여는 귀하가 우리에게 기여를 사용할 권리를 부여할 권리가 있음을 선언하는 기여자 라이선스 계약(CLA)에 동의해야 합니다. 자세한 내용은 [CLA, 기여자 라이선스 계약 웹사이트](https://cla.microsoft.com?WT.mc_id=academic-105485-koreyst)를 참조하세요.

중요: 이 레포지토리의 텍스트를 번역할 때는 기계 번역을 사용하지 않도록 주의해 주세요. 우리는 커뮤니티를 통해 번역을 검증할 것이므로, 능숙한 언어에 대해서만 번역을 자원해 주세요.

Pull Request를 제출하면 CLA-bot이 자동으로 CLA를 제공해야 하는지 여부를 결정하고 PR에 적절히 표시합니다(예: 라벨, 댓글). 봇이 제공하는 지침을 따르기만 하면 됩니다. 이 작업은 우리의 CLA를 사용하는 모든 레포지토리에서 한 번만 수행하면 됩니다.

이 프로젝트는 [Microsoft 오픈 소스 행동 강령](https://opensource.microsoft.com/codeofconduct/?WT.mc_id=academic-105485-koreyst)을 채택했습니다. 자세한 내용은 행동 강령 FAQ를 읽거나 추가 질문이나 의견이 있으면 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.

## 시작해 봅시다

이제 이 코스를 완료하는 데 필요한 단계를 완료했으니, [생성형 AI와 LLM 소개](../../../01-introduction-to-genai/translations/ko/README.md?WT.mc_id=academic-105485-koreyst)부터 시작해 봅시다.

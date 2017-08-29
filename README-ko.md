# PixieDust와 Jupyter Notebook를 활용하여 페이스북에서 인사이트 찾아내기

이 개발자 과정에서는 Jupyter 노트북을 사용하여 방대한 양의 구조화되지 않은 데이터에서 통찰력을 수집합니다. 초기 노트북 디자인을 제공해 준 [Anna Quincy](https://www.linkedin.com/in/anna-quincy-25042957)과 [Tyler Andersen](https://www.linkedin.com/in/tyler-andersen-2bb82336)에게 감사의 말씀을 전합니다.

Facebook Analytics에서 내 보낸 데이터로 시작하여, Natural Language Understanding (NLU), Tone Analyzer, Visual Recognition 의 왓슨 API로 데이터를 풍부하게 만듭니다. 

다음과 같은 질문에 대답하기 위해 이 데이터를 사용합니다 :

> 글에 표현된 가장 보편적인 감정/감성 상태는 무엇이고, 참여도가 가장 높은 게시물은 무엇인지?

> 글에 표현된 어조, 언급된 주요 대상, 참여 호응도 간의 관계는 무엇입니까?

이러한 유형의 통찰력은 브랜드 인지도, 제품 성능, 고객 만족도 및 고객 참여도를 이해하고 향상시키는 데 관심이있는 마케팅 분석가에게 유용합니다. 

이 개발자 과정은 한 세트의 결과를 내는 응용 프로그램이 아니라 여러 실험을 안내하기 위한 용도로 작성 되었습니다. 표준 Facebook Analytics 내보내기에는 좋아요(likes), 공유(shares) 및 노출(impression)과 같은 표준 Facebook 성능 측정 항목과 함께, 내가 쓴 글, 기사 및 썸네일로 부터 텍스트를 내보낼 수 있습니다. 이러한 구조화되지 않은 콘텐츠로부터 Watson API를 통해 키워드, 엔터티, 감정(정서) 및 어조를 추출할 수 있습니다. 

데이터가 Watson API로 풍부해 지면 이를 분석 할 수 있는 몇 가지 방법이 있습니다. Data Science Experience는 강력하면서도 유연한 Facebook 콘텐츠 탐색 방법을 제공합니다.

이 개발자 과정은 가상의 Facebook 데이터 및 쥬피터 노트북 환경 그리고, 숨겨진 통찰력을 발견하는 데 필요한 사전 준비된 시각화 툴이 제공됩니다.

이 과정을 마치면 다음과 같은 것을 이해하게 될 것입니다 :

 * DSX Object Storage 및 pandas DataFrame을 통해 외부 데이터를 Jupyter Notebook으로 읽어 들입니다.
 * Jupyter Notebook 및 왓슨 API를 사용하여 구조화되지 않은 데이터를 풍부하게 합니다 :
     * [Natural Language Understanding](https://www.ibm.com/watson/developercloud/natural-language-understanding.html)
     * [Tone Analyzer](https://www.ibm.com/watson/developercloud/tone-analyzer.html)
     * [Visual Recognition](https://www.ibm.com/watson/developercloud/visual-recognition.html)
 * DSX Jupyter 노트의 pandas DataFrame에서 DSX Object Storage의 파일로 데이터를 씁니다.
 * [PixieDust](https://github.com/ibm-cds-labs/pixiedust)를 사용하여 데이터를 시각화하고 탐색할 수 있게 됩니다.

![](doc/source/images/architecture.png)

## 흐름도
1. Facebook Analytics에서 내 보낸 CSV 파일이 DSX Object Storage에 추가됩니다.
2. 생성 된 코드는 파일을 pandas DataFrame으로 액세스 할 수 있게 합니다.
3. 데이터는 Watson Natural Language Understanding을 통해 추가 정보가 채워집니다.
4. 데이터는 Watson Tone Analyzer를 통해 추가 정보가 채워집니다.
5. 데이터는 Watson Visual Recognition를 통해 추가 정보가 채워집니다.
6. 이렇게 가공된 데이터는 PixieDust를 통해, 숨겨진 인사이트를 발견하고 이를 강조하기 위해 그래프를 만들 수 있습니다.

## With Watson

Watson 애플리케이션의 다음 레벨로 넘어가고 싶으신가요? Watson 브랜드 자산을 활용하고 싶으신가요? 독점적 브랜드, 마케팅, 기술 리소스를 제공하는 [With Watson](https://www.ibm.com/watson/with-watson) 프로그램에 참여하시면 Watson을 활용한 여러분의 상용 솔루션의 가치를 높일 수 있습니다.

# 구성 요소

* [IBM Data Science Experience](https://www.ibm.com/bs-en/marketplace/data-science-experience): RStudio, Jupyter, Python에 매니지드 Spark, 협업 환경 등의 부가 서비가 함께 제공되는 데이터 분석 환경
* [Bluemix Object Storage](https://console.ng.bluemix.net/catalog/services/object-storage/?cm_sp=dw-bluemix-_-code-_-devcenter): 빠른 시장 진입과 고가용성 및 비용 효과적인 어플리케이션을 만들기 위한 클라우드 기반 비정형 데이터 저장 서비스
* [Watson Natural Language Understanding](https://www.ibm.com/watson/developercloud/natural-language-understanding.html): 고급 텍스트 분석을 위한 자연어 처리
* [Watson Tone Analyzer](https://www.ibm.com/watson/developercloud/tone-analyzer.html): 텍스트의 대화 톤을 감지하기 위해 언어학적 분석을 활용함
* [Visual Recognition](https://www.ibm.com/watson/developercloud/visual-recognition.html): 이미지 내용을 이해

# 주요 기술

* [Jupyter Notebooks](http://jupyter.org/): 라이브 코드, 방정식, 시각화 및 설명 텍스트가 포함 된 문서를 만들고 공유 할 수 있는 오픈 소스 웹 응용 프로그램
* [PixieDust](https://github.com/ibm-cds-labs/pixiedust): 데이터 작업 경험을 향상시키기 위해 Jupyter 노트북의 추가 기능으로 작동하는 오픈 소스 헬퍼 라이브러리
* [pandas](http://pandas.pydata.org/): 고성능의 사용하기 쉬운 데이터 구조를 제공하는 Python 라이브러리

* [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/): HTML 및 XML 파일에서 데이터를 가져 오는 Python 라이브러리

* [Data Science](https://developer.ibm.com/code/technologies/data-science/): 인사이트 추출을 위한 정형 데이터 및 비정형 데이터 분석 시스템 및 방법

* [Cognitive](https://developer.ibm.com/watson/): 왓슨은 인간처럼 생각할 수 있는 인지 기술
* [Analytics](https://developer.ibm.com/code/technologies/analytics/): 분석을 통한 기업의 데이터 가치 제공
* [Python](https://www.python.org/): Python은 보다 신속하게 작업하고 시스템을 보다 효과적으로 통합 할 수 있게 해주는 프로그래밍 언어

# 비디오 보기

[![](http://img.youtube.com/vi/UIkjFo9o3vI/0.jpg)](https://www.youtube.com/watch?v=UIkjFo9o3vI)

# 절차

이 개발자의 여행을 설정하고 실행하려면 다음 단계를 따르십시오. 단계는 아래에서 자세히 설명합니다.

1. [Data Science Experience 가입하기](#1-data-science-experience-가입하기)
1. [노트북 만들기](#2-노트북-만들기)
1. [Bluemix 서비스 만들기](#3-bluemix-서비스-만들기)
1. [자격 증명 추가](#4-자격-증명-추가)
1. [CSV 파일 추가](#5-csv-파일-추가)
1. [노트북 실행하기](#6-노트북-실행하기)
1. [결과 분석](#7-결과-분석)
1. [작업 저장](#8-작업-저장)

## 1. Data Science Experience 가입하기

IBM의 [Data Science Experience](http://datascience.ibm.com/)에 가입 하십시오. Data Science Experience (DSX) 에 가입함으로써, 두 서비스: ``DSX-Spark`` 및 ``DSX-ObjectStore`` 서비스가 Bluemix 계정에 생성됩니다.

## 2. 노트북 만들기

이 git repo에 있는 노트북의 URL을 사용하여 DSX에서 노트북을 만들 수 있습니다. (또는 저장소를 복제 한 경우 로컬 파일로 부터 가능)

[Data Science Experience](http://datascience.ibm.com/)에 로그인 합니다.

1. 왼쪽에있는 메뉴를 사용하여, `Projects` 선택 후 `Default Project` 선택합니다.
1. `add notebooks` (오른편 위쪽) 를 클릭하여, 노트북을 생성합니다.
1. `From URL` 탭을 선택합니다.
1. 노트북의 이름을 입력하십시오.
1. 선택적으로, 노트북에 대한 설명을 입력하십시오.
1. 아래의 노트북 URL를 입력하십시오:
    ```
    https://github.com/IBM/pixiedust-facebook-analysis/blob/master/notebooks/pixiedust_facebook_analysis.ipynb
    ```
1. `Create Notebook` 버튼을 클릭하십시오.

![](doc/source/images/create_notebook_from_url.png)

## 3. Bluemix 서비스 만들기

`Deploy to Bluemix` 를 클릭하여 다음의 Bluemix 서비스들을 만들거나, 아래의 링크를 사용하여 Bluemix UI에서 서비스를 만듭니다.

  * [**Visual Recognition**](https://console.ng.bluemix.net/catalog/services/visual-recognition)
  * [**Natural Language Understanding**](https://console.ng.bluemix.net/catalog/services/natural-language-understanding)
  * [**Tone Analyzer**](https://console.ng.bluemix.net/catalog/services/tone-analyzer)
  
[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/ibm/pixiedust-facebook-analysis)

## 4. 자격 증명 추가

`1.5. Add Service Credentials From Bluemix for Watson Services` 다음에 있는 셀을 노트북에서 찾습니다.

다섯 개의 <add _...> 라는 곳에 블루믹스 `Service Credentials` 의 탭에 있는 정보로 바꿉니다. Bluemix 대시 보드를 사용하여 각 서비스를 찾고 해당 `Service Credentials` 탭을 클릭 하십시오. 경우에 따라서는 `New Credential` 옵션을 사용하여 자격 증명을 만들어야 할 수 있습니다.

![](doc/source/images/add_credentials.png)

> Note: 이 셀은 중요한 자격 증명을 포함하기 때문에 `hidden_cell` 로 표시됩니다.

## 5. CSV 파일 추가

#### CSV 파일을 노트북에 추가하십시오.
`Find and Add Data` (`10/01` 아이콘을 찾으십시오) 및 `Files` 탭을 사용하십시오.
`browse`를 선택하여, 컴퓨터에 있는 .csv 파일을 추가하십시오.

![](doc/source/images/add_file.png)

> Note:  나만의 데이터가 없으면 이 git repo 를 복제하여 예제 데이터를 얻을 수 있습니다. `data/example_input`에 위치합니다.

#### 코드에 추가하기
노트북에서 `2.1 Load data from Object Storage` 셀을 찾아, `# Insert pandas DataFrame` 뒤에 커서를 놓습니다. 코드를 삽입하기 전에 이 셀이 선택되어 있는지 확인하십시오.

위에 추가 한 파일 (10/01 파일 탭 아래)을 사용하여(under the 10/01 Files tab),
`Insert to code` 드롭 다운 메뉴에서 `Insert Pandas DataFrame` 를 선택합니다.

![](doc/source/images/insert_to_code.png)

> Note: 이 셀에는 민감한 자격 증명이 포함되어 있기 때문에 hidden_cell 로 표시됩니다.

![](doc/source/images/inserted_pandas.png)

#### 변수명 수정
The inserted code includes a generated method with credentials and then calls
the generated method to set a variable with a name like `df_data_1`. If you do
additional inserts, the method can be re-used and the variable will change
(e.g. `df_data_2`).

Later in the notebook, we set `df = df_data_1`. So you might need to
fix the variable name `df_data_1` to match your inserted code or vice versa.

#### Add file credentials

We want to write the enriched file to the same container that we used above. So now we'll use the same file drop-down to insert credentials. We'll use them later when we write out the enriched CSV file.

After the `df` setup, there is a cell to enter the file credentials.
Place your cursor after the `#insert credentials for file - Change to credentials_1` line. Make sure this cell is selected before inserting credentials.

Use the CSV file's drop-down menu again. This time select `Insert Credentials`.

![](doc/source/images/insert_file_credentials.png)

Note: 이 셀에는 민감한 자격 증명이 포함되어 있기 때문에 hidden_cell 로 표시됩니다.

#### 변수명 수정
추가된 코드에는 `credentials_1`와 유사한 이름의 변수에 자격 증명이 저장됩니다
다른 이름 (예를 들어, `credentials_2`)일 수도 있으니, 필요에 따라 변경합니다. `credentials_1`를 가정하여 작성되어 있습니다.

## 6. 노트북 실행하기

노트가 실행될 때 실제로 일어나는 것은 노트의 각 코드 셀이 위에서 아래로 순서대로 실행된다는 것입니다.

각 코드 셀은 선택 가능하며 왼쪽 부분에 태그가 붙습니다. 태그 형식은 `In [x]:` 입니다. 노트북의 상태에 따라 `x` 값은 다음과 같습니다.:

* 공백: 셀이 한 번도 실행되지 않았음을 나타냅니다.
* 숫자: 해당 셀이 실행된 상대적인 순서를 나타냅니다.
* `*`: 셀이 현재 실행 중임을 나타냅니다.

노트북에서 코드 셀을 실행하는 데는 여러 가지 방법이 있습니다.:

* 한 번에 하나의 셀 실행.
  * 셀을 선택한 다음 툴바에서 `Play` 버튼을 누릅니다.
* 배치모드: 순서대로 실행.
  * `Cell` 메뉴 모음에 사용할 수 있는 몇 가지 옵션이 있습니다. 예를 들어, `Run All`을 통해 모든 셀을 모두 실행하거나, `Run All Below`을 통해 현재 셀 바로 아래 셀로 부터 가장 아래 마지막까지 계속 실행할 수 있습니다.
* 스케쥴 기반
  * 노트북 패널의 오른쪽 상단에 있는 `Schedule` 버튼을 누릅니다. 여기서 스케쥴 기반으로 한 번 또는 지정된 간격으로 반복적으로 노트북을 실행하도록 예약할 수 있습니다.

## 7. 결과 분석

### Part I - 데이터 풍부하게 하기

각각의 셀을 살펴보면, Part I에서 다음을 수행한다는 것을 알수 있습니다 :

* PyPI에서 외부 라이브러리 설치
* Watson 인지 서비스에 연결하는 클라이언트 생성
* 로컬 CSV 파일의 데이터를 (Object Storage를 통해) pandas DataFrame으로 로드
* pandas로 데이터 조작하기
* BeautifulSoup 사용하기
* Natural Language Understanding 사용하기
* Tone Analyzer 사용하기
* Visual Recognition 사용하기
* CSV 파일을 Object Storage에 저장하기

### Part II - 데이터 준비

Part II에서는 pandas를 사용하여 메인 DataFrame 으로 부터, 여러 개의 DataFrames를 만듭니다. 슬라이싱과 다이싱 및 클리닝 후에, 이 새로운 DataFrames는 PixieDust에 사용될 준비가 됩니다.

### Part III - 분석

Part III 에서는 PixieDust를 사용하여 여러 메트릭을 탐색하고 시각화하여 결과를 분석합니다.

이전에 수행 한 모든 준비 작업이 끝나면 PixieDust 덕분에 별도의 코드가 거의 필요 없다는 것을 알 수 있습니다. 단지, 아래와 같은 한 줄 짜리 코드만 필요합니다 :
```python
display(<data-frame>)
```

```display(tones)```라는 것을 두 개의 다른 셀에서 사용했지만, 서로 다른 결과가 나옵니다. PixieDust에게 데이터를 표시하는 방법을 알려주기 위해 셀 메타 데이터를 사용했습니다. `Edit Metadata` 메뉴를 확인하십시오. 보이지 않으면, View > Cell Toolbar > Edit Metadata를 사용하여 표시되도록 설정하십시오. 처음 두 차트의 메타 데이터를 보면, 막대 차트와 원형 차트가 어떻게 표시되는지 알 수 있습니다.

**PixieDust는 상호 반응형 (interactive)입니다!** 여러 조작을 통해 새로운 인사이트를 탐구할 수 있습니다.

`Options` 버튼을 사용하여 차트 설정을 변경합니다. 첫 번째 차트는 게시물에서 감지된 감정에 의한 포스트 소비를 보여줍니다. 집계 유형을 SUM에서 AVG로 변경하여 다른 결론을 얻을 수도 있습니다. 각 감정의 빈도를 확인하려면 COUNT (으)로 변경할 수도 있습니다.

다음을 시도해보십시오 :
* 감정 톤 대신 키로 사회적 톤을 사용하십시오.(또는 둘 다)
* 사용자에 대한 부정적인 피드백과 같은 다른 측정 항목을 시도하십시오.
* 다른 렌더러를 사용해보십시오.
* 다른 차트 유형 (및 표)을 사용해보십시오.

여러 조합을 통해 페이스북 게시물의 영향도와 관련된 통찰력을 갖게 됩니다. 이를 통해 설득력 있는 최상의 프레젠테이션을 찾으십시오.

## 8. 작업 저장

### 작업 저장 방법:

`File` 메뉴에는, 노트북을 저장하는 몇 가지 방법이 있습니다 :

* `Save` 버전 정보없이 노트북의 현재 상태를 저장합니다.
* `Save Version` 은 날짜 및 시간 스탬프가 포함된 버전 태그로 노트북의 현재 상태를 저장합니다. 최대 10개의 버전으로 저장할 수 있으며 Revert To Version 메뉴 항목을 선택하여 되돌릴 수 있습니다.

# 샘플 결과

data/examples의 결과 예제에는 PixieDust 차트 용 JavaScript가 내장되어 있습니다. github 페이지를 통해 살펴보십시오: [here](https://ibm.github.io/pixiedust-facebook-analysis/data/examples/pixiedust_facebook_analysis.html)

> Note: HTML예제는 몇가지 인터렉티브한 기능이 동작하지 않습니다. 전체 기능을 사용하려면 노트북을 실행하십시오. 출력없이 코드 및 마크 다운 셀을 보려면 github 뷰어로 [notebooks/pixiedust_facebook_analysis.ipynb](notebooks/pixiedust_facebook_analysis.ipynb)를 볼 수 있습니다.

# 링크

PixieDust에 대한 자세한 내용은 다음을 확인하십시오 :
* PixieDust 문서: https://ibm-cds-labs.github.io/pixiedust/index.html
* PixieDust GitHub Repo: https://github.com/ibm-cds-labs/pixiedust

추가적인 코드 패턴을 확인하려면 Watson Accelerators 포털을 방문하십시오.
* Watson Accelerators: http://www.watsonaccelerators.com

# 라이센스

[Apache 2.0](LICENSE)

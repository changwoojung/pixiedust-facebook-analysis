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

Watson 응용 프로그램을 다음 단계로 가져 가고 싶습니까? Watson 브랜드 자산을 활용하고 싶습니까? Watson이 포함된 상용화 솔루션의 성공을 가속화하기 위해 독점적인 브랜드, 마케팅 및 기술 리소스를 제공 하는 [With Watson](https://www.ibm.com/watson/with-watson) 프로그램에 가입하십시오.

# 구성 요소

* [IBM Data Science Experience](https://www.ibm.com/bs-en/marketplace/data-science-experience): Analyze data using RStudio, Jupyter, and Python in a configured, collaborative environment that includes IBM value-adds, such as managed Spark.
* [Bluemix Object Storage](https://console.ng.bluemix.net/catalog/services/object-storage/?cm_sp=dw-bluemix-_-code-_-devcenter): A Bluemix service that provides an unstructured cloud data store to build and deliver cost effective apps and services with high reliability and fast speed to market.
* [Watson Natural Language Understanding](https://www.ibm.com/watson/developercloud/natural-language-understanding.html): Natural language processing for advanced text analysis.
* [Watson Tone Analyzer](https://www.ibm.com/watson/developercloud/tone-analyzer.html): Uses linguistic analysis to detect communication tones in written text.
* [Visual Recognition](https://www.ibm.com/watson/developercloud/visual-recognition.html): Understand image content.

# 주요 기술

* [Jupyter Notebooks](http://jupyter.org/): An open-source web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.
* [PixieDust](https://github.com/ibm-cds-labs/pixiedust): PixieDust is an open source helper library that works as an add-on to Jupyter notebooks to improve the user experience of working with data.
* [pandas](http://pandas.pydata.org/): A Python library providing high-performance, easy-to-use data structures.
* [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/): Beautiful Soup is a Python library for pulling data out of HTML and XML files.
* [Data Science](https://developer.ibm.com/code/technologies/data-science/): Systems and scientific methods to analyze structured and unstructured data in order to extract knowledge and insights.
* [Cognitive](https://developer.ibm.com/watson/): Watson is a cognitive technology that can think like a human.
* [Analytics](https://developer.ibm.com/code/technologies/analytics/): Analytics delivers the value of data for the enterprise.
* [Python](https://www.python.org/): Python is a programming language that lets you work more quickly and integrate your systems more effectively.

# 비디오 보기

[![](http://img.youtube.com/vi/UIkjFo9o3vI/0.jpg)](https://www.youtube.com/watch?v=UIkjFo9o3vI)

# 절차

이 개발자의 여행을 설정하고 실행하려면 다음 단계를 따르십시오. 단계는 아래에서 자세히 설명합니다.

1. [Sign up for the Data Science Experience](#1-sign-up-for-the-data-science-experience)
1. [Create the notebook](#2-create-the-notebook)
1. [Create Bluemix services](#3-create-bluemix-services)
1. [Add credentials](#4-add-credentials)
1. [Add the CSV file](#5-add-the-csv-file)
1. [Run the notebook](#6-run-the-notebook)
1. [Analyze the results](#7-analyze-the-results)
1. [Save your work](#8-save-your-work)

## 1. Sign up for the Data Science Experience

Sign up for IBM's [Data Science Experience](http://datascience.ibm.com/). By signing up for the Data Science Experience, two services: ``DSX-Spark`` and ``DSX-ObjectStore`` will be created in your Bluemix account.

## 2. Create the notebook

You can create the notebook in DSX using the URL of the notebook that is in this git repo (or similarly from a local file if you cloned the repo).

1. Use the menu on the left to select `My Projects` and then `Default Project`.
1. Click on `Add notebooks` (upper right) to create a notebook.
1. Select the `From URL` tab.
1. Enter a name for the notebook.
1. Optionally, enter a description for the notebook.
1. Enter this Notebook URL:
    ```
    https://github.com/IBM/pixiedust-facebook-analysis/blob/master/notebooks/pixiedust_facebook_analysis.ipynb
    ```
1. Click the `Create Notebook` button.

![](doc/source/images/create_notebook_from_url.png)

## 3. Create Bluemix services

Create the following Bluemix services by clicking the `Deploy to Bluemix` button, or use these links to create the services in the Bluemix UI.

  * [**Visual Recognition**](https://console.ng.bluemix.net/catalog/services/visual-recognition)
  * [**Natural Language Understanding**](https://console.ng.bluemix.net/catalog/services/natural-language-understanding)
  * [**Tone Analyzer**](https://console.ng.bluemix.net/catalog/services/tone-analyzer)
  
[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/ibm/pixiedust-facebook-analysis)

## 4. Add credentials

Find the notebook cell after `1.5. Add Service Credentials From Bluemix for Watson Services`.

Replace the five <add_...> placeholder values with information from the `Service Credentials` tab in Bluemix. Use your Bluemix dashboard to find each of the services and click on the `Service Credentials` tab. In some cases, you might need to create credentials with the `New Credential` option.

![](doc/source/images/add_credentials.png)

> Note: This cell is marked as a `hidden_cell` because it will contain sensitive credentials.

## 5. Add the CSV file

#### Add the CSV file to the notebook
Use `Find and Add Data` (look for the `10/01` icon)
and its `Files` tab. From there you can click
`browse` and add a .csv file from your computer.

![](doc/source/images/add_file.png)

> Note:  If you don't have your own data, you can get our example by cloning
this git repo. Look in the `data/example_input` directory.

#### Insert to code
Find the notebook cell after `2.1 Load data from Object Storage`. Place your cursor after `# Insert pandas DataFrame`. Make sure this cell is selected before inserting code.

Using the file that you added above (under the 10/01 Files tab),
use the `Insert to code` drop-down menu.
Select `Insert Pandas DataFrame` from the drop-down menu.

![](doc/source/images/insert_to_code.png)

> Note: This cell is marked as a hidden_cell because it contains
sensitive credentials.

![](doc/source/images/inserted_pandas.png)

#### Fix-up variable names
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

Note: This cell is marked as a `hidden_cell` because it contains sensitive credentials.

#### Fix-up variable names
The inserted code includes a dictionary with credentials assigned to a variable
with a name like `credentials_1`. It may have a different name (e.g. `credentials_2`).
Rename it or reassign it if needed. The notebook code assumes it will be `credentials_1`.

## 6. 노트북 

When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.
* At a scheduled time.
  * Press the `Schedule` button located in the top right section of your notebook
    panel. Here you can schedule your notebook to be executed once at some future
    time, or repeatedly at your specified interval.

## 7. 결과 분석

### Part I - Enrich

If you walk through the cells, you will see that we demonstrated how to do the following in Part I:

* Install external libraries from PyPI
* Create clients to connect to Watson cognitive services
* Load data from a local CSV file to a pandas DataFrame (via Object Storage)
* Do some data manipulation with pandas
* Use BeautifulSoup
* Use Natural Language Understanding
* Use Tone Analyzer
* Use Visual Recognition
* Save the enriched data in a CSV file in Object Storage

### Part II - Data Preparation

In Part II, we used pandas to create multiple DataFrames from our main enriched DataFrame. After slicing and dicing and cleaning, these new DataFrames are ready for PixieDust to use.

### Part III - Analyze

In Part III, we analyze the results by exploring and visualizing the metrics with PixieDust.

After all the prep work done earlier, you'll see that there is almost no code
needed here (thanks to PixieDust). We just use one-liners like this:
```python
display(<data-frame>)
```

You should also notice that we used ```display(tones)``` in two different
cells, but the result was two different charts. How can that happen?
Well, we used cell metadata to tell PixieDust how to display the data.
Notice the `Edit Metadata` button on each cell. If you don't see it, use the menu
`View > Cell Toolbar > Edit Metadata` to make it visible. If you look at
the metadata for the first two charts, you'll see how we got a bar chart and a pie chart.

**PixieDust is interactive!** This is where we explore to find out what
the enriched data will tell us.

Use the `Options` button to change the chart settings. The first chart shows
post consumption by the detected emotion in the article. Notice how changing
the aggregation type from SUM to AVG gives you a very different conclusion.
You can also change it to COUNT to see the frequency of each emotion, but when you do that the metric no longer matters.

Explore by trying the following:
* Use social tone as the key instead of emotion tone (or both).
* Try other metrics such as lifetime negative feedback from users. 
* Try the different renderers.
* Try different chart types (and a grid).

The right combination will give you insights into the impact of
your facebook posts. Once you uncover the insights, find the best
presentation to convince others.

## 8. 작업 저장

### 작업 저장 방법:

Under the `File` menu, there are several ways to save your notebook:

* `Save` will simply save the current state of your notebook, without any version
  information.
* `Save Version` will save your current state of your notebook with a version tag
  that contains a date and time stamp. Up to 10 versions of your notebook can be
  saved, each one retrievable by selecting the `Revert To Version` menu item.

# 샘플 결과

The example output in data/examples has embedded JavaScript for
PixieDust charts. View it via github pages: [here](https://ibm.github.io/pixiedust-facebook-analysis/data/examples/pixiedust_facebook_analysis.html)

> Note: Some interactive functionality does not work in the HTML sample. Run the notebook for full functionality. To see the code and markdown cells without output, you can view [notebooks/pixiedust_facebook_analysis.ipynb](notebooks/pixiedust_facebook_analysis.ipynb) with the github viewer.

# 링크

For more information about PixieDust, check out the following:
* PixieDust Documentation: https://ibm-cds-labs.github.io/pixiedust/index.html
* PixieDust GitHub Repo: https://github.com/ibm-cds-labs/pixiedust

Visit the Watson Accelerators portal to see more live patterns in action:
* Watson Accelerators: http://www.watsonaccelerators.com

# 라이센스

[Apache 2.0](LICENSE)

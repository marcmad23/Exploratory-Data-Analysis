# Exploratory Data Analysis to help plan Clinical Trials
[Data Source​ Website](https://data.cms.gov/provider-data/dataset/mj5m-pzi6)

Data Dictionary: https://data.cms.gov/provider-data/sites/default/files/data_dictionaries/physician/DOC_Data_Dictionary.pdf

[Exploratory Data Analysis Tutorials](https://www.analyticsvidhya.com/blog/2021/02/introduction-to-exploratory-data-analysis-eda/)



# Summary
The goal of this project was to help people plan clinical trails by creating a dataset of doctors including their location, their speciality, and whether they had clinical trial experience.  To create this dataset, I used data about doctors from [cms.gov](https://data.cms.gov/provider-data/dataset/mj5m-pzi6) and clinicaltrials.gov.  I used pandas to clean and merge the datasets together. After successfully merging the data, I wrote functions to help people query the data and also created visualizations of the data to help people understand what the dataset I created contained. 


---



---



![top_10_spec.png](data:image/png;base64,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)

Above I have pulled a count of the top 10 primary specialties found in the created dataset.

#### Some insights before cleaning dataset
* Many NPI values are repeating due to doctors and clinicians working at multiple locations.
* Certain organizatons have the same name, but have different addresses, might have to be wary while cleaning.
* Phone number column is in float data type, many of them are decimals to a power of 10

#### Created bulleted list to note down observations made while looking at dataset
* There is quite a significant amount of null cells in this dataset.
* NPI contains no nulls, through here we can identify how many doctors are represented.
* NPI however does include many duplicates, this is due to doctors and clinicians having multiple entries in the dataset
* There are 1674853 duplicated NPI entries, when removed it contained 1212388 entries.
* For the middle name column there is a mix of nulls, full middle names, and initals.

#### Questions about dataset
* Is there any other way to get accurate phone numbers, changing the data type will round the number to nearest integer.
* Will removing depeating NPI's affect the information I can retrieve from this dataset?
* Are we specifically focusing on the US?



# 1. Importing packages
These packages will help me manipulate and clean the data more efficiently 


```python
import pandas as pd
pd.set_option('display.max_columns', None)
import matplotlib.pyplot as plt
import numpy as np
import os
```


```python
from google.colab import drive
drive.mount('/content/drive')
```

    Mounted at /content/drive



```python
# This cell downloads the data from the cms website
! wget https://data.cms.gov/provider-data/sites/default/files/resources/69a75aa9d3dc1aed6b881725cf0ddc12_1658503878/DAC_NationalDownloadableFile.csv 
```

    --2022-08-08 17:11:37--  https://data.cms.gov/provider-data/sites/default/files/resources/69a75aa9d3dc1aed6b881725cf0ddc12_1658503878/DAC_NationalDownloadableFile.csv
    Resolving data.cms.gov (data.cms.gov)... 23.73.254.125, 2600:1408:c400:1889::28a, 2600:1408:c400:1882::28a
    Connecting to data.cms.gov (data.cms.gov)|23.73.254.125|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 729485319 (696M) [text/csv]
    Saving to: ‘DAC_NationalDownloadableFile.csv’
    
    DAC_NationalDownloa 100%[===================>] 695.69M  91.2MB/s    in 8.1s    
    
    2022-08-08 17:11:45 (86.3 MB/s) - ‘DAC_NationalDownloadableFile.csv’ saved [729485319/729485319]
    



```python
# Running ls shows us that the DAC_NationalDownnloadableFile.csv is available in the local filesystem for this notebook
! ls
```

    DAC_NationalDownloadableFile.csv  drive  sample_data



```python
# This line reads in the file to a pandas dataframe
df = pd.read_csv('DAC_NationalDownloadableFile.csv',encoding_errors='ignore',low_memory=False)
```


```python
# Now we view the top of the dataframe
df.head(10)
```





  <div id="df-d9970250-5008-46f8-a53e-7618e0fb8039">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NPI</th>
      <th>Ind_PAC_ID</th>
      <th>Ind_enrl_ID</th>
      <th>lst_nm</th>
      <th>frst_nm</th>
      <th>mid_nm</th>
      <th>suff</th>
      <th>gndr</th>
      <th>Cred</th>
      <th>Med_sch</th>
      <th>Grd_yr</th>
      <th>pri_spec</th>
      <th>sec_spec_1</th>
      <th>sec_spec_2</th>
      <th>sec_spec_3</th>
      <th>sec_spec_4</th>
      <th>sec_spec_all</th>
      <th>org_nm</th>
      <th>org_pac_id</th>
      <th>num_org_mem</th>
      <th>adr_ln_1</th>
      <th>adr_ln_2</th>
      <th>ln_2_sprs</th>
      <th>cty</th>
      <th>st</th>
      <th>zip</th>
      <th>phn_numbr</th>
      <th>hosp_afl_1</th>
      <th>hosp_afl_lbn_1</th>
      <th>hosp_afl_2</th>
      <th>hosp_afl_lbn_2</th>
      <th>hosp_afl_3</th>
      <th>hosp_afl_lbn_3</th>
      <th>hosp_afl_4</th>
      <th>hosp_afl_lbn_4</th>
      <th>hosp_afl_5</th>
      <th>hosp_afl_lbn_5</th>
      <th>ind_assgn</th>
      <th>grp_assgn</th>
      <th>adrs_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1215327325</td>
      <td>1658616016</td>
      <td>I20181213001362</td>
      <td>PAONE</td>
      <td>MARGARET</td>
      <td>E</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2014.0</td>
      <td>CLINICAL SOCIAL WORKER</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>677 STATE ROUTE 17M</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MONROE</td>
      <td>NY</td>
      <td>109503318</td>
      <td>8.452065e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY109503318MO677XX17MX400</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1215901749</td>
      <td>7618952888</td>
      <td>I20040622000465</td>
      <td>ISLAM</td>
      <td>ABUL</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>MD</td>
      <td>OTHER</td>
      <td>1970.0</td>
      <td>HEMATOLOGY</td>
      <td>PATHOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>PATHOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>100 HIGH ST</td>
      <td>RM E318</td>
      <td>NaN</td>
      <td>BUFFALO</td>
      <td>NY</td>
      <td>142031126</td>
      <td>7.168596e+09</td>
      <td>330005.0</td>
      <td>KALEIDA HEALTH</td>
      <td>330102</td>
      <td>KENMORE MERCY HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>NY142031126BU100XXSTXX309</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1215294566</td>
      <td>7719296813</td>
      <td>I20151012000381</td>
      <td>REYNA MALDONADO</td>
      <td>EDGAR</td>
      <td>D</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2002.0</td>
      <td>FAMILY PRACTICE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2270 JOE BATTLE BLVD</td>
      <td>NaN</td>
      <td>Y</td>
      <td>EL PASO</td>
      <td>TX</td>
      <td>799382610</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>TX799382610EL2270XBLVD400</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1215331699</td>
      <td>2668791369</td>
      <td>I20150430001727</td>
      <td>HALDEMAN</td>
      <td>STEPHANIE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2014.0</td>
      <td>PHYSICIAN ASSISTANT</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>15601 N 28TH AVE</td>
      <td>SUITE 100</td>
      <td>NaN</td>
      <td>PHOENIX</td>
      <td>AZ</td>
      <td>850534061</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>AZ850534061PH15601AVEX401</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1215397526</td>
      <td>7315245800</td>
      <td>I20160418000391</td>
      <td>FOX</td>
      <td>THOMAS</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>PALMER COLLEGE CHIROPRACTIC -  WEST SUNNYVALE</td>
      <td>2015.0</td>
      <td>CHIROPRACTIC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>524 E 2ND ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>LEXINGTON</td>
      <td>KY</td>
      <td>40508</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>KY405080000LE524XXSTXX400</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1215481908</td>
      <td>2769769173</td>
      <td>I20170511001220</td>
      <td>BROCKA</td>
      <td>ERIC</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2015.0</td>
      <td>CHIROPRACTIC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>95 WILLMAN ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>HIAWATHA</td>
      <td>IA</td>
      <td>522331518</td>
      <td>3.199390e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>IA522331518HI95XXXSTXX300</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1215346887</td>
      <td>3577808849</td>
      <td>I20181214002965</td>
      <td>HUGHES</td>
      <td>JESSICA</td>
      <td>ANDREA</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2017.0</td>
      <td>CLINICAL PSYCHOLOGIST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1455 FRAZEE RD</td>
      <td>SUITE 500</td>
      <td>NaN</td>
      <td>SAN DIEGO</td>
      <td>CA</td>
      <td>921084350</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>CA921084350SA1455XRDXX301</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1215574447</td>
      <td>244665982</td>
      <td>I20200210000758</td>
      <td>SZARABAJKA</td>
      <td>CHIARRA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2010.0</td>
      <td>PHYSICAL THERAPY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1503 GAUSE BLVD</td>
      <td>SUITE 6</td>
      <td>NaN</td>
      <td>SLIDELL</td>
      <td>LA</td>
      <td>704582246</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>LA704582246SL1503XBLVD301</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1215462932</td>
      <td>648537464</td>
      <td>I20171204002947</td>
      <td>BAGGETT</td>
      <td>BLAKE</td>
      <td>ANTHONY</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>LIFE CHIROPRACTIC COLLEGE</td>
      <td>2017.0</td>
      <td>CHIROPRACTIC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>917 MCFARLAND BLVD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NORTHPORT</td>
      <td>AL</td>
      <td>354763373</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>AL354763373NO917XXBLVD300</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1215343884</td>
      <td>3577981802</td>
      <td>I20210105000304</td>
      <td>STONE</td>
      <td>VALERIE</td>
      <td>ELAINE</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2017.0</td>
      <td>CLINICAL PSYCHOLOGIST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8241 W POMONA DR</td>
      <td>HOME OFFICE</td>
      <td>NaN</td>
      <td>ARVADA</td>
      <td>CO</td>
      <td>800052572</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>CO800052572AR8241XDRXX401</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-d9970250-5008-46f8-a53e-7618e0fb8039')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-d9970250-5008-46f8-a53e-7618e0fb8039 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-d9970250-5008-46f8-a53e-7618e0fb8039');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




# 2. Cleaning first dataset
Used fuctions like `.info` and `.shape` to gain insight on data that I would be working with


```python
# Here we check how big the dataframe is
df.shape
```




    (2364224, 40)




```python
print(df.columns)
#Certain columns seem to having trailing spaces in their names we should try to remove them
```

    Index(['NPI', ' Ind_PAC_ID', ' Ind_enrl_ID', ' lst_nm', ' frst_nm', ' mid_nm',
           ' suff', ' gndr', ' Cred', ' Med_sch', ' Grd_yr', ' pri_spec',
           ' sec_spec_1', '    sec_spec_2', ' sec_spec_3', ' sec_spec_4',
           ' sec_spec_all', '    org_nm', ' org_pac_id', ' num_org_mem',
           ' adr_ln_1', ' adr_ln_2', ' ln_2_sprs', ' cty', ' st', ' zip',
           ' phn_numbr', '    hosp_afl_1', ' hosp_afl_lbn_1', ' hosp_afl_2',
           ' hosp_afl_lbn_2', ' hosp_afl_3', ' hosp_afl_lbn_3', ' hosp_afl_4',
           ' hosp_afl_lbn_4', ' hosp_afl_5', ' hosp_afl_lbn_5', ' ind_assgn',
           ' grp_assgn', ' adrs_id'],
          dtype='object')



```python
df.columns = df.columns.str.strip()
print(df.columns)
#Now the column names have been trimmed and will be easier to work with
```

    Index(['NPI', 'Ind_PAC_ID', 'Ind_enrl_ID', 'lst_nm', 'frst_nm', 'mid_nm',
           'suff', 'gndr', 'Cred', 'Med_sch', 'Grd_yr', 'pri_spec', 'sec_spec_1',
           'sec_spec_2', 'sec_spec_3', 'sec_spec_4', 'sec_spec_all', 'org_nm',
           'org_pac_id', 'num_org_mem', 'adr_ln_1', 'adr_ln_2', 'ln_2_sprs', 'cty',
           'st', 'zip', 'phn_numbr', 'hosp_afl_1', 'hosp_afl_lbn_1', 'hosp_afl_2',
           'hosp_afl_lbn_2', 'hosp_afl_3', 'hosp_afl_lbn_3', 'hosp_afl_4',
           'hosp_afl_lbn_4', 'hosp_afl_5', 'hosp_afl_lbn_5', 'ind_assgn',
           'grp_assgn', 'adrs_id'],
          dtype='object')



```python
df.info()
#using info to check on basic info about dataset such as column name and data type
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 2364224 entries, 0 to 2364223
    Data columns (total 40 columns):
     #   Column          Dtype  
    ---  ------          -----  
     0   NPI             int64  
     1   Ind_PAC_ID      int64  
     2   Ind_enrl_ID     object 
     3   lst_nm          object 
     4   frst_nm         object 
     5   mid_nm          object 
     6   suff            object 
     7   gndr            object 
     8   Cred            object 
     9   Med_sch         object 
     10  Grd_yr          float64
     11  pri_spec        object 
     12  sec_spec_1      object 
     13  sec_spec_2      object 
     14  sec_spec_3      object 
     15  sec_spec_4      object 
     16  sec_spec_all    object 
     17  org_nm          object 
     18  org_pac_id      float64
     19  num_org_mem     float64
     20  adr_ln_1        object 
     21  adr_ln_2        object 
     22  ln_2_sprs       object 
     23  cty             object 
     24  st              object 
     25  zip             object 
     26  phn_numbr       float64
     27  hosp_afl_1      float64
     28  hosp_afl_lbn_1  object 
     29  hosp_afl_2      object 
     30  hosp_afl_lbn_2  object 
     31  hosp_afl_3      object 
     32  hosp_afl_lbn_3  object 
     33  hosp_afl_4      object 
     34  hosp_afl_lbn_4  object 
     35  hosp_afl_5      float64
     36  hosp_afl_lbn_5  object 
     37  ind_assgn       object 
     38  grp_assgn       object 
     39  adrs_id         object 
    dtypes: float64(6), int64(2), object(32)
    memory usage: 721.5+ MB



```python
#checking how many nulls are present and whether or not they will have an impact on the analysis results
df.isnull().sum()
```




    NPI                     0
    Ind_PAC_ID              0
    Ind_enrl_ID             0
    lst_nm                 42
    frst_nm                34
    mid_nm             678560
    suff              2326595
    gndr                    0
    Cred              1762423
    Med_sch                 5
    Grd_yr               1461
    pri_spec                0
    sec_spec_1        2041301
    sec_spec_2        2329692
    sec_spec_3        2360676
    sec_spec_4        2363621
    sec_spec_all      2041301
    org_nm             161458
    org_pac_id         161454
    num_org_mem        161454
    adr_ln_1                0
    adr_ln_2          1533661
    ln_2_sprs         2214763
    cty                     0
    st                      0
    zip                     0
    phn_numbr          370070
    hosp_afl_1         723689
    hosp_afl_lbn_1     766488
    hosp_afl_2        1569124
    hosp_afl_lbn_2    1581555
    hosp_afl_3        1953009
    hosp_afl_lbn_3    1956632
    hosp_afl_4        2127424
    hosp_afl_lbn_4    2129345
    hosp_afl_5        2213610
    hosp_afl_lbn_5    2214908
    ind_assgn               0
    grp_assgn               0
    adrs_id                 0
    dtype: int64




```python
#Checking for how many distinct NPI's are present, since the column contains 0 nulls
len(df.NPI.unique())
```




    1208486




```python
#Because the other ID's also contain 0 nulls I will make sure they match the amount of distinct values present under NPI
len(df.Ind_PAC_ID.unique())
```




    1208488




```python
len(df.Ind_enrl_ID.unique())
```




    1264113




```python
len(df.adrs_id.unique())
```




    347390




```python
df[df.duplicated(['NPI'], keep=False)]
#Here I used  df.duplicated() to locate which rows were duplicates based off NPI
```





  <div id="df-14bd285d-adab-4c97-8669-56942911d858">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NPI</th>
      <th>Ind_PAC_ID</th>
      <th>Ind_enrl_ID</th>
      <th>lst_nm</th>
      <th>frst_nm</th>
      <th>mid_nm</th>
      <th>suff</th>
      <th>gndr</th>
      <th>Cred</th>
      <th>Med_sch</th>
      <th>Grd_yr</th>
      <th>pri_spec</th>
      <th>sec_spec_1</th>
      <th>sec_spec_2</th>
      <th>sec_spec_3</th>
      <th>sec_spec_4</th>
      <th>sec_spec_all</th>
      <th>org_nm</th>
      <th>org_pac_id</th>
      <th>num_org_mem</th>
      <th>adr_ln_1</th>
      <th>adr_ln_2</th>
      <th>ln_2_sprs</th>
      <th>cty</th>
      <th>st</th>
      <th>zip</th>
      <th>phn_numbr</th>
      <th>hosp_afl_1</th>
      <th>hosp_afl_lbn_1</th>
      <th>hosp_afl_2</th>
      <th>hosp_afl_lbn_2</th>
      <th>hosp_afl_3</th>
      <th>hosp_afl_lbn_3</th>
      <th>hosp_afl_4</th>
      <th>hosp_afl_lbn_4</th>
      <th>hosp_afl_5</th>
      <th>hosp_afl_lbn_5</th>
      <th>ind_assgn</th>
      <th>grp_assgn</th>
      <th>adrs_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1215901749</td>
      <td>7618952888</td>
      <td>I20040622000465</td>
      <td>ISLAM</td>
      <td>ABUL</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>MD</td>
      <td>OTHER</td>
      <td>1970.0</td>
      <td>HEMATOLOGY</td>
      <td>PATHOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>PATHOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>100 HIGH ST</td>
      <td>RM E318</td>
      <td>NaN</td>
      <td>BUFFALO</td>
      <td>NY</td>
      <td>142031126</td>
      <td>7.168596e+09</td>
      <td>330005.0</td>
      <td>KALEIDA HEALTH</td>
      <td>330102</td>
      <td>KENMORE MERCY HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>NY142031126BU100XXSTXX309</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1215294566</td>
      <td>7719296813</td>
      <td>I20151012000381</td>
      <td>REYNA MALDONADO</td>
      <td>EDGAR</td>
      <td>D</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2002.0</td>
      <td>FAMILY PRACTICE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2270 JOE BATTLE BLVD</td>
      <td>NaN</td>
      <td>Y</td>
      <td>EL PASO</td>
      <td>TX</td>
      <td>799382610</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>TX799382610EL2270XBLVD400</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1215331699</td>
      <td>2668791369</td>
      <td>I20150430001727</td>
      <td>HALDEMAN</td>
      <td>STEPHANIE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2014.0</td>
      <td>PHYSICIAN ASSISTANT</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>15601 N 28TH AVE</td>
      <td>SUITE 100</td>
      <td>NaN</td>
      <td>PHOENIX</td>
      <td>AZ</td>
      <td>850534061</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>AZ850534061PH15601AVEX401</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1215343884</td>
      <td>3577981802</td>
      <td>I20210105000304</td>
      <td>STONE</td>
      <td>VALERIE</td>
      <td>ELAINE</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2017.0</td>
      <td>CLINICAL PSYCHOLOGIST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8241 W POMONA DR</td>
      <td>HOME OFFICE</td>
      <td>NaN</td>
      <td>ARVADA</td>
      <td>CO</td>
      <td>800052572</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>CO800052572AR8241XDRXX401</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1215376108</td>
      <td>7416199583</td>
      <td>I20161109000294</td>
      <td>ABRAHAM</td>
      <td>TINA</td>
      <td>E</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>MICHIGAN STATE UNIVERSITY COLLEGE OF OSTEOPATH...</td>
      <td>2013.0</td>
      <td>ALLERGY/IMMUNOLOGY</td>
      <td>INTERNAL MEDICINE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>INTERNAL MEDICINE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1083 SUNCREST DR</td>
      <td>SUITE B</td>
      <td>NaN</td>
      <td>LAPEER</td>
      <td>MI</td>
      <td>484464421</td>
      <td>NaN</td>
      <td>230193.0</td>
      <td>MCLAREN LAPEER REGION</td>
      <td>230207</td>
      <td>MCLAREN OAKLAND</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>MI484464421LA1083XDRXX301</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2364214</th>
      <td>1730120387</td>
      <td>840257317</td>
      <td>I20041216000096</td>
      <td>STANLEY</td>
      <td>LEWIS</td>
      <td>A</td>
      <td>NaN</td>
      <td>M</td>
      <td>CNA</td>
      <td>STATE UNIVERSITY OF NEW YORK AT BUFFALO SCHOOL...</td>
      <td>1990.0</td>
      <td>CERTIFIED REGISTERED NURSE ANESTHETIST (CRNA)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>INNOVATIVE ANESTHESIA SOLUTIONS LLC</td>
      <td>9.931595e+09</td>
      <td>11.0</td>
      <td>35 HOSPITAL RD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>BLAIRSVILLE</td>
      <td>GA</td>
      <td>305123139</td>
      <td>NaN</td>
      <td>111324.0</td>
      <td>CHATUGE REGIONAL HOSPITAL</td>
      <td>110051</td>
      <td>UNION GENERAL HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>Y</td>
      <td>GA305123139BL35XXXRDXX300</td>
    </tr>
    <tr>
      <th>2364215</th>
      <td>1790253185</td>
      <td>2769449313</td>
      <td>I20181115003110</td>
      <td>BASS</td>
      <td>LONNIE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2018.0</td>
      <td>CERTIFIED REGISTERED NURSE ANESTHETIST (CRNA)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>INNOVATIVE ANESTHESIA SOLUTIONS LLC</td>
      <td>9.931595e+09</td>
      <td>11.0</td>
      <td>110 S MAIN ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>HIAWASSEE</td>
      <td>GA</td>
      <td>305463408</td>
      <td>7.068962e+09</td>
      <td>110051.0</td>
      <td>UNION GENERAL HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>GA305463408HI110XXSTXX400</td>
    </tr>
    <tr>
      <th>2364216</th>
      <td>1790253185</td>
      <td>2769449313</td>
      <td>I20181115003110</td>
      <td>BASS</td>
      <td>LONNIE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2018.0</td>
      <td>CERTIFIED REGISTERED NURSE ANESTHETIST (CRNA)</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>INNOVATIVE ANESTHESIA SOLUTIONS LLC</td>
      <td>9.931595e+09</td>
      <td>11.0</td>
      <td>35 HOSPITAL RD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>BLAIRSVILLE</td>
      <td>GA</td>
      <td>305123139</td>
      <td>NaN</td>
      <td>110051.0</td>
      <td>UNION GENERAL HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>GA305123139BL35XXXRDXX300</td>
    </tr>
    <tr>
      <th>2364220</th>
      <td>1952926776</td>
      <td>9638598683</td>
      <td>I20200924003127</td>
      <td>CHILDERS</td>
      <td>MASON</td>
      <td>BUCKLEY</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>UNIVERSITY ALABAMA BIRMINGHAM  - SCHOOL OF OPT...</td>
      <td>2020.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>WIREGRASS EYE CARE OF OZARK, PC</td>
      <td>9.931598e+09</td>
      <td>2.0</td>
      <td>231 E BROAD ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>OZARK</td>
      <td>AL</td>
      <td>363601507</td>
      <td>3.058031e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>AL363601507OZ231XXSTXX400</td>
    </tr>
    <tr>
      <th>2364221</th>
      <td>1811202716</td>
      <td>446428627</td>
      <td>I20110713000454</td>
      <td>LANGFORD</td>
      <td>MATTHEW</td>
      <td>STEPHEN</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>ILLINOIS COLLEGE OF OPTOMETRY AT CHICAGO</td>
      <td>2010.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M LANGFORD OD OPTOMETRIC CORPORATION</td>
      <td>9.931600e+09</td>
      <td>3.0</td>
      <td>4310 GENESEE AVE</td>
      <td>SUITE 101</td>
      <td>NaN</td>
      <td>SAN DIEGO</td>
      <td>CA</td>
      <td>921174936</td>
      <td>8.585605e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>CA921174936SA4310XAVEX302</td>
    </tr>
  </tbody>
</table>
<p>1657197 rows × 40 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-14bd285d-adab-4c97-8669-56942911d858')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-14bd285d-adab-4c97-8669-56942911d858 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-14bd285d-adab-4c97-8669-56942911d858');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
#Now that I know that duplicates are present I will remove them
df = df.drop_duplicates('NPI', keep='last')
df
#Now that dataframe contains 1212388 NPI values
```





  <div id="df-83190882-5257-431a-870b-cdd5b9e309a5">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NPI</th>
      <th>Ind_PAC_ID</th>
      <th>Ind_enrl_ID</th>
      <th>lst_nm</th>
      <th>frst_nm</th>
      <th>mid_nm</th>
      <th>suff</th>
      <th>gndr</th>
      <th>Cred</th>
      <th>Med_sch</th>
      <th>Grd_yr</th>
      <th>pri_spec</th>
      <th>sec_spec_1</th>
      <th>sec_spec_2</th>
      <th>sec_spec_3</th>
      <th>sec_spec_4</th>
      <th>sec_spec_all</th>
      <th>org_nm</th>
      <th>org_pac_id</th>
      <th>num_org_mem</th>
      <th>adr_ln_1</th>
      <th>adr_ln_2</th>
      <th>ln_2_sprs</th>
      <th>cty</th>
      <th>st</th>
      <th>zip</th>
      <th>phn_numbr</th>
      <th>hosp_afl_1</th>
      <th>hosp_afl_lbn_1</th>
      <th>hosp_afl_2</th>
      <th>hosp_afl_lbn_2</th>
      <th>hosp_afl_3</th>
      <th>hosp_afl_lbn_3</th>
      <th>hosp_afl_4</th>
      <th>hosp_afl_lbn_4</th>
      <th>hosp_afl_5</th>
      <th>hosp_afl_lbn_5</th>
      <th>ind_assgn</th>
      <th>grp_assgn</th>
      <th>adrs_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1215327325</td>
      <td>1658616016</td>
      <td>I20181213001362</td>
      <td>PAONE</td>
      <td>MARGARET</td>
      <td>E</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2014.0</td>
      <td>CLINICAL SOCIAL WORKER</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>677 STATE ROUTE 17M</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MONROE</td>
      <td>NY</td>
      <td>109503318</td>
      <td>8.452065e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY109503318MO677XX17MX400</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1215397526</td>
      <td>7315245800</td>
      <td>I20160418000391</td>
      <td>FOX</td>
      <td>THOMAS</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>PALMER COLLEGE CHIROPRACTIC -  WEST SUNNYVALE</td>
      <td>2015.0</td>
      <td>CHIROPRACTIC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>524 E 2ND ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>LEXINGTON</td>
      <td>KY</td>
      <td>40508</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>KY405080000LE524XXSTXX400</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1215481908</td>
      <td>2769769173</td>
      <td>I20170511001220</td>
      <td>BROCKA</td>
      <td>ERIC</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2015.0</td>
      <td>CHIROPRACTIC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>95 WILLMAN ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>HIAWATHA</td>
      <td>IA</td>
      <td>522331518</td>
      <td>3.199390e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>IA522331518HI95XXXSTXX300</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1215346887</td>
      <td>3577808849</td>
      <td>I20181214002965</td>
      <td>HUGHES</td>
      <td>JESSICA</td>
      <td>ANDREA</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2017.0</td>
      <td>CLINICAL PSYCHOLOGIST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1455 FRAZEE RD</td>
      <td>SUITE 500</td>
      <td>NaN</td>
      <td>SAN DIEGO</td>
      <td>CA</td>
      <td>921084350</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>CA921084350SA1455XRDXX301</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1215574447</td>
      <td>244665982</td>
      <td>I20200210000758</td>
      <td>SZARABAJKA</td>
      <td>CHIARRA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2010.0</td>
      <td>PHYSICAL THERAPY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1503 GAUSE BLVD</td>
      <td>SUITE 6</td>
      <td>NaN</td>
      <td>SLIDELL</td>
      <td>LA</td>
      <td>704582246</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>LA704582246SL1503XBLVD301</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2364219</th>
      <td>1568088722</td>
      <td>5193140739</td>
      <td>I20200730000687</td>
      <td>CHILDERS</td>
      <td>GISELLE</td>
      <td>PACHECO</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>UNIVERSITY ALABAMA BIRMINGHAM  - SCHOOL OF OPT...</td>
      <td>2020.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>WIREGRASS EYE CARE OF OZARK, PC</td>
      <td>9.931598e+09</td>
      <td>2.0</td>
      <td>231 E BROAD ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>OZARK</td>
      <td>AL</td>
      <td>363601507</td>
      <td>3.058031e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>AL363601507OZ231XXSTXX400</td>
    </tr>
    <tr>
      <th>2364220</th>
      <td>1952926776</td>
      <td>9638598683</td>
      <td>I20200924003127</td>
      <td>CHILDERS</td>
      <td>MASON</td>
      <td>BUCKLEY</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>UNIVERSITY ALABAMA BIRMINGHAM  - SCHOOL OF OPT...</td>
      <td>2020.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>WIREGRASS EYE CARE OF OZARK, PC</td>
      <td>9.931598e+09</td>
      <td>2.0</td>
      <td>231 E BROAD ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>OZARK</td>
      <td>AL</td>
      <td>363601507</td>
      <td>3.058031e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>AL363601507OZ231XXSTXX400</td>
    </tr>
    <tr>
      <th>2364221</th>
      <td>1811202716</td>
      <td>446428627</td>
      <td>I20110713000454</td>
      <td>LANGFORD</td>
      <td>MATTHEW</td>
      <td>STEPHEN</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>ILLINOIS COLLEGE OF OPTOMETRY AT CHICAGO</td>
      <td>2010.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M LANGFORD OD OPTOMETRIC CORPORATION</td>
      <td>9.931600e+09</td>
      <td>3.0</td>
      <td>4310 GENESEE AVE</td>
      <td>SUITE 101</td>
      <td>NaN</td>
      <td>SAN DIEGO</td>
      <td>CA</td>
      <td>921174936</td>
      <td>8.585605e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>CA921174936SA4310XAVEX302</td>
    </tr>
    <tr>
      <th>2364222</th>
      <td>1952394777</td>
      <td>6901837848</td>
      <td>I20050830000724</td>
      <td>SNEAG</td>
      <td>GARY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>OD</td>
      <td>PENNSYLVANIA COLLEGE OF OPTOMETRY</td>
      <td>1993.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M LANGFORD OD OPTOMETRIC CORPORATION</td>
      <td>9.931600e+09</td>
      <td>3.0</td>
      <td>4310 GENESEE AVE</td>
      <td>SUITE 101</td>
      <td>NaN</td>
      <td>SAN DIEGO</td>
      <td>CA</td>
      <td>921174936</td>
      <td>8.585605e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>CA921174936SA4310XAVEX302</td>
    </tr>
    <tr>
      <th>2364223</th>
      <td>1902112477</td>
      <td>3173789229</td>
      <td>I20120718000499</td>
      <td>LANGFORD</td>
      <td>MELANIE</td>
      <td>J</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>ILLINOIS COLLEGE OF OPTOMETRY AT CHICAGO</td>
      <td>2010.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M LANGFORD OD OPTOMETRIC CORPORATION</td>
      <td>9.931600e+09</td>
      <td>3.0</td>
      <td>4310 GENESEE AVE</td>
      <td>SUITE 101</td>
      <td>NaN</td>
      <td>SAN DIEGO</td>
      <td>CA</td>
      <td>921174936</td>
      <td>8.585605e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>CA921174936SA4310XAVEX302</td>
    </tr>
  </tbody>
</table>
<p>1208486 rows × 40 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-83190882-5257-431a-870b-cdd5b9e309a5')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-83190882-5257-431a-870b-cdd5b9e309a5 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-83190882-5257-431a-870b-cdd5b9e309a5');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 1208486 entries, 0 to 2364223
    Data columns (total 40 columns):
     #   Column          Non-Null Count    Dtype  
    ---  ------          --------------    -----  
     0   NPI             1208486 non-null  int64  
     1   Ind_PAC_ID      1208486 non-null  int64  
     2   Ind_enrl_ID     1208486 non-null  object 
     3   lst_nm          1208457 non-null  object 
     4   frst_nm         1208473 non-null  object 
     5   mid_nm          864337 non-null   object 
     6   suff            18994 non-null    object 
     7   gndr            1208486 non-null  object 
     8   Cred            287228 non-null   object 
     9   Med_sch         1208482 non-null  object 
     10  Grd_yr          1207708 non-null  float64
     11  pri_spec        1208486 non-null  object 
     12  sec_spec_1      136276 non-null   object 
     13  sec_spec_2      13434 non-null    object 
     14  sec_spec_3      1528 non-null     object 
     15  sec_spec_4      291 non-null      object 
     16  sec_spec_all    136276 non-null   object 
     17  org_nm          1077863 non-null  object 
     18  org_pac_id      1077867 non-null  float64
     19  num_org_mem     1077867 non-null  float64
     20  adr_ln_1        1208486 non-null  object 
     21  adr_ln_2        441846 non-null   object 
     22  ln_2_sprs       38820 non-null    object 
     23  cty             1208486 non-null  object 
     24  st              1208486 non-null  object 
     25  zip             1208486 non-null  object 
     26  phn_numbr       1047286 non-null  float64
     27  hosp_afl_1      735944 non-null   float64
     28  hosp_afl_lbn_1  726632 non-null   object 
     29  hosp_afl_2      301686 non-null   object 
     30  hosp_afl_lbn_2  297995 non-null   object 
     31  hosp_afl_3      133025 non-null   object 
     32  hosp_afl_lbn_3  131805 non-null   object 
     33  hosp_afl_4      63764 non-null    object 
     34  hosp_afl_lbn_4  63224 non-null    object 
     35  hosp_afl_5      33497 non-null    float64
     36  hosp_afl_lbn_5  33205 non-null    object 
     37  ind_assgn       1208486 non-null  object 
     38  grp_assgn       1208486 non-null  object 
     39  adrs_id         1208486 non-null  object 
    dtypes: float64(6), int64(2), object(32)
    memory usage: 378.0+ MB


# 3. Reading other data necessary for this analysis
This data will also be cleaned and then merged to create accurate records of clinical trials



```python
#imported both files into notebook
facilities = pd.read_csv("/content/drive/MyDrive/data for internship/facilities.csv")
facility_investigators = pd.read_csv("/content/drive/MyDrive/data for internship/facility_investigators.csv")
#Now will use head() to get a quick look at data
```

    /usr/local/lib/python3.7/dist-packages/IPython/core/interactiveshell.py:2882: DtypeWarning: Columns (2) have mixed types.Specify dtype option on import or set low_memory=False.
      exec(code_obj, self.user_global_ns, self.user_ns)



```python
facilities.head()
```





  <div id="df-5d9e8606-0b08-4db7-add4-c5f8ed8dc40c">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>name</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163635</td>
      <td>NCT04072887</td>
      <td>NaN</td>
      <td>Novartis Investigative Site</td>
      <td>Andalusia</td>
      <td>Alabama</td>
      <td>36420</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>1</th>
      <td>53628563</td>
      <td>NCT03432260</td>
      <td>NaN</td>
      <td>DURECT Study Site 0001</td>
      <td>San Diego</td>
      <td>California</td>
      <td>92118</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54846233</td>
      <td>NCT01806571</td>
      <td>NaN</td>
      <td>Mayo Clinic in Arizona</td>
      <td>Scottsdale</td>
      <td>Arizona</td>
      <td>85259</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163636</td>
      <td>NCT04072887</td>
      <td>NaN</td>
      <td>Novartis Investigative Site</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90025</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163637</td>
      <td>NCT04072887</td>
      <td>NaN</td>
      <td>Novartis Investigative Site</td>
      <td>Westminster</td>
      <td>California</td>
      <td>92683</td>
      <td>United States</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-5d9e8606-0b08-4db7-add4-c5f8ed8dc40c')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-5d9e8606-0b08-4db7-add4-c5f8ed8dc40c button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-5d9e8606-0b08-4db7-add4-c5f8ed8dc40c');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
facility_investigators.head()
```





  <div id="df-ca23e561-7e83-443b-99fb-cafd23db9a04">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>nct_id</th>
      <th>facility_id</th>
      <th>role</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6092264</td>
      <td>NCT05033743</td>
      <td>53017259</td>
      <td>Principal Investigator</td>
      <td>Chemen Neal, MD</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6092265</td>
      <td>NCT05033743</td>
      <td>53017259</td>
      <td>Sub-Investigator</td>
      <td>David Haas, MD, MS</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6092266</td>
      <td>NCT05033743</td>
      <td>53017259</td>
      <td>Sub-Investigator</td>
      <td>Peipert Jeffrey, MD, PhD</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6314742</td>
      <td>NCT03505801</td>
      <td>55091850</td>
      <td>Principal Investigator</td>
      <td>Stephen Mester, MD</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6226691</td>
      <td>NCT04136002</td>
      <td>53911630</td>
      <td>Principal Investigator</td>
      <td>Pankaj Kashyap, MD</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-ca23e561-7e83-443b-99fb-cafd23db9a04')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-ca23e561-7e83-443b-99fb-cafd23db9a04 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-ca23e561-7e83-443b-99fb-cafd23db9a04');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
facilities.info()
#id and nct_id have no nulls, will check for duplicates later
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 2709619 entries, 0 to 2709618
    Data columns (total 8 columns):
     #   Column   Dtype 
    ---  ------   ----- 
     0   id       int64 
     1   nct_id   object
     2   status   object
     3   name     object
     4   city     object
     5   state    object
     6   zip      object
     7   country  object
    dtypes: int64(1), object(7)
    memory usage: 165.4+ MB



```python
facility_investigators.info()
#no nulls present, will check for duplicates just to make sure
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 220483 entries, 0 to 220482
    Data columns (total 5 columns):
     #   Column       Non-Null Count   Dtype 
    ---  ------       --------------   ----- 
     0   id           220483 non-null  int64 
     1   nct_id       220483 non-null  object
     2   facility_id  220483 non-null  int64 
     3   role         220483 non-null  object
     4   name         220483 non-null  object
    dtypes: int64(2), object(3)
    memory usage: 8.4+ MB



```python
len(facilities.id.unique())
#no repeating ids in facilities dataframe
```




    2709619




```python
len(facilities.nct_id.unique())
#some repeating values in this column, needs a more in depth look
```




    374524




```python
len(facility_investigators.id.unique())
#no repeating values, these are doctor ids. May be the key for merging with NAC datatset
```




    220483




```python
len(facility_investigators.nct_id.unique())
#some repeating values, will check out later
```




    40991




```python
len(facility_investigators.facility_id.unique())
#Repeating values, a look at dataframe as a whole might help
#Some investigators were at the same facility hence the repating values
```




    169820



Going to change the id column in the facilities dataframe into facility_id so it can be easily merged.



```python
facilities = facilities.rename({"id":"facility_id"}, axis = 1)
facilities.head()
#id was updated to facility_id, now i merge
```





  <div id="df-ba6ac23b-adb5-441e-9f14-bced3b3253a6">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>name</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163635</td>
      <td>NCT04072887</td>
      <td>NaN</td>
      <td>Novartis Investigative Site</td>
      <td>Andalusia</td>
      <td>Alabama</td>
      <td>36420</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>1</th>
      <td>53628563</td>
      <td>NCT03432260</td>
      <td>NaN</td>
      <td>DURECT Study Site 0001</td>
      <td>San Diego</td>
      <td>California</td>
      <td>92118</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54846233</td>
      <td>NCT01806571</td>
      <td>NaN</td>
      <td>Mayo Clinic in Arizona</td>
      <td>Scottsdale</td>
      <td>Arizona</td>
      <td>85259</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163636</td>
      <td>NCT04072887</td>
      <td>NaN</td>
      <td>Novartis Investigative Site</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90025</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163637</td>
      <td>NCT04072887</td>
      <td>NaN</td>
      <td>Novartis Investigative Site</td>
      <td>Westminster</td>
      <td>California</td>
      <td>92683</td>
      <td>United States</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-ba6ac23b-adb5-441e-9f14-bced3b3253a6')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-ba6ac23b-adb5-441e-9f14-bced3b3253a6 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-ba6ac23b-adb5-441e-9f14-bced3b3253a6');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
len(facilities.facility_id.unique())

```




    2709619



# 4. Used pandas to merge datasets based on columns
Data within both data sets had been cleaned prior to the merge, however it still must be cleaned after merge as well.


```python
clinical_trials= facilities.merge(facility_investigators, how="inner", on=["facility_id", "nct_id"])
clinical_trials.head(10)
#merged above, used head to see if anything looked messed up
```





  <div id="df-92c4a47d-feac-49d0-baf3-cd08982371dd">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>name_x</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name_y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163791</td>
      <td>NCT04056910</td>
      <td>Recruiting</td>
      <td>UPMC Hillman Cancer Center</td>
      <td>Pittsburgh</td>
      <td>Pennsylvania</td>
      <td>15232</td>
      <td>United States</td>
      <td>6272018</td>
      <td>Principal Investigator</td>
      <td>Jason J Luke, MD, FACP</td>
    </tr>
    <tr>
      <th>1</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272019</td>
      <td>Sub-Investigator</td>
      <td>Alice Luca, MSc</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272020</td>
      <td>Sub-Investigator</td>
      <td>Jose Carvalho, MD</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272021</td>
      <td>Sub-Investigator</td>
      <td>John Kingdom, MD</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272022</td>
      <td>Sub-Investigator</td>
      <td>Chinaza Egbuta, PhD</td>
    </tr>
    <tr>
      <th>5</th>
      <td>52531058</td>
      <td>NCT00168493</td>
      <td>Recruiting</td>
      <td>Baker Heart Research Institute</td>
      <td>Melbourne</td>
      <td>Victoria</td>
      <td>3</td>
      <td>Australia</td>
      <td>6049365</td>
      <td>Principal Investigator</td>
      <td>David a Barton, m</td>
    </tr>
    <tr>
      <th>6</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272023</td>
      <td>Principal Investigator</td>
      <td>Alexander P Dudgeon, PhD</td>
    </tr>
    <tr>
      <th>7</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272024</td>
      <td>Sub-Investigator</td>
      <td>Catherine A Kendall, PhD</td>
    </tr>
    <tr>
      <th>8</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272025</td>
      <td>Sub-Investigator</td>
      <td>Charlie Hall, MBBS</td>
    </tr>
    <tr>
      <th>9</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272026</td>
      <td>Sub-Investigator</td>
      <td>Maryam Nowghani</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-92c4a47d-feac-49d0-baf3-cd08982371dd')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-92c4a47d-feac-49d0-baf3-cd08982371dd button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-92c4a47d-feac-49d0-baf3-cd08982371dd');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
#used info to make sure math adds up or at least makes some sort of sense
clinical_trials.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 220483 entries, 0 to 220482
    Data columns (total 11 columns):
     #   Column       Non-Null Count   Dtype 
    ---  ------       --------------   ----- 
     0   facility_id  220483 non-null  int64 
     1   nct_id       220483 non-null  object
     2   status       206976 non-null  object
     3   name_x       220469 non-null  object
     4   city         220483 non-null  object
     5   state        151053 non-null  object
     6   zip          193729 non-null  object
     7   country      220483 non-null  object
     8   id           220483 non-null  int64 
     9   role         220483 non-null  object
     10  name_y       220483 non-null  object
    dtypes: int64(2), object(9)
    memory usage: 20.2+ MB


Now that we have the newly merged dataset, we must merge it with the DAC file. However, we need identify which columns can be merged on eachother.


```python
clinical_trials = clinical_trials.rename({"name_x":"facility_name"}, axis = 1)
clinical_trials = clinical_trials.rename({"name_y":"name"},axis = 1)
clinical_trials.head()
#Just cleaning up the names of the columns
```





  <div id="df-522395df-34ca-4889-9178-075cf2843f10">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163791</td>
      <td>NCT04056910</td>
      <td>Recruiting</td>
      <td>UPMC Hillman Cancer Center</td>
      <td>Pittsburgh</td>
      <td>Pennsylvania</td>
      <td>15232</td>
      <td>United States</td>
      <td>6272018</td>
      <td>Principal Investigator</td>
      <td>Jason J Luke, MD, FACP</td>
    </tr>
    <tr>
      <th>1</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272019</td>
      <td>Sub-Investigator</td>
      <td>Alice Luca, MSc</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272020</td>
      <td>Sub-Investigator</td>
      <td>Jose Carvalho, MD</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272021</td>
      <td>Sub-Investigator</td>
      <td>John Kingdom, MD</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272022</td>
      <td>Sub-Investigator</td>
      <td>Chinaza Egbuta, PhD</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-522395df-34ca-4889-9178-075cf2843f10')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-522395df-34ca-4889-9178-075cf2843f10 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-522395df-34ca-4889-9178-075cf2843f10');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
df = df.rename({"cty":"city"}, axis = 1)
df = df.rename({"st":"state"}, axis = 1)
df.columns
```




    Index(['NPI', 'Ind_PAC_ID', 'Ind_enrl_ID', 'lst_nm', 'frst_nm', 'mid_nm',
           'suff', 'gndr', 'Cred', 'Med_sch', 'Grd_yr', 'pri_spec', 'sec_spec_1',
           'sec_spec_2', 'sec_spec_3', 'sec_spec_4', 'sec_spec_all', 'org_nm',
           'org_pac_id', 'num_org_mem', 'adr_ln_1', 'adr_ln_2', 'ln_2_sprs',
           'city', 'state', 'zip', 'phn_numbr', 'hosp_afl_1', 'hosp_afl_lbn_1',
           'hosp_afl_2', 'hosp_afl_lbn_2', 'hosp_afl_3', 'hosp_afl_lbn_3',
           'hosp_afl_4', 'hosp_afl_lbn_4', 'hosp_afl_5', 'hosp_afl_lbn_5',
           'ind_assgn', 'grp_assgn', 'adrs_id'],
          dtype='object')



# 5. Here I begin to seperate the names present in the merged dataset
This is so it can merge with the medicare enrollment data, name is in a certain format so it must be matched.


```python
#now going to split name column from clinical trials into frst_nm, mid_nm, lst_nm, and Cred
#However, credentials in this dataset are delimitted by a comma, so we have to do the name and credentials separately
clinical_trials[['name','Cred']]= clinical_trials['name'].str.split(',', n=1, expand = True)
clinical_trials.head(10)
```





  <div id="df-50160d51-e7df-4b30-99d8-551179d3ee11">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163791</td>
      <td>NCT04056910</td>
      <td>Recruiting</td>
      <td>UPMC Hillman Cancer Center</td>
      <td>Pittsburgh</td>
      <td>Pennsylvania</td>
      <td>15232</td>
      <td>United States</td>
      <td>6272018</td>
      <td>Principal Investigator</td>
      <td>Jason J Luke</td>
      <td>MD, FACP</td>
    </tr>
    <tr>
      <th>1</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272019</td>
      <td>Sub-Investigator</td>
      <td>Alice Luca</td>
      <td>MSc</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272020</td>
      <td>Sub-Investigator</td>
      <td>Jose Carvalho</td>
      <td>MD</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272021</td>
      <td>Sub-Investigator</td>
      <td>John Kingdom</td>
      <td>MD</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272022</td>
      <td>Sub-Investigator</td>
      <td>Chinaza Egbuta</td>
      <td>PhD</td>
    </tr>
    <tr>
      <th>5</th>
      <td>52531058</td>
      <td>NCT00168493</td>
      <td>Recruiting</td>
      <td>Baker Heart Research Institute</td>
      <td>Melbourne</td>
      <td>Victoria</td>
      <td>3</td>
      <td>Australia</td>
      <td>6049365</td>
      <td>Principal Investigator</td>
      <td>David a Barton</td>
      <td>m</td>
    </tr>
    <tr>
      <th>6</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272023</td>
      <td>Principal Investigator</td>
      <td>Alexander P Dudgeon</td>
      <td>PhD</td>
    </tr>
    <tr>
      <th>7</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272024</td>
      <td>Sub-Investigator</td>
      <td>Catherine A Kendall</td>
      <td>PhD</td>
    </tr>
    <tr>
      <th>8</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272025</td>
      <td>Sub-Investigator</td>
      <td>Charlie Hall</td>
      <td>MBBS</td>
    </tr>
    <tr>
      <th>9</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>Gloucester</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272026</td>
      <td>Sub-Investigator</td>
      <td>Maryam Nowghani</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-50160d51-e7df-4b30-99d8-551179d3ee11')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-50160d51-e7df-4b30-99d8-551179d3ee11 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-50160d51-e7df-4b30-99d8-551179d3ee11');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
clinical_trials['array'] = clinical_trials['name'].str.split(' ')
#this was done to create a list of arrays of the names, so I could seperate the first and last name ignoring the middle name
```


```python
clinical_trials['frst_nm']= clinical_trials['array'].apply(lambda x: x[0])
#clinical_trials['array']= clinical_trials['array'].apply(lambda x: x[0])+ ' ' +clinical_trials['array'].apply(lambda x: x[-1])
#This code allowed me to get the first and last name, now we can split the column into frst_nm and lst_nm which we can merge on
```


```python
clinical_trials['lst_nm']= clinical_trials['array'].apply(lambda x: x[-1])
clinical_trials.head()
```





  <div id="df-0bf3ba1c-8f7a-4ef7-b91c-067f9eaf4025">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred</th>
      <th>array</th>
      <th>frst_nm</th>
      <th>lst_nm</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163791</td>
      <td>NCT04056910</td>
      <td>Recruiting</td>
      <td>UPMC Hillman Cancer Center</td>
      <td>Pittsburgh</td>
      <td>Pennsylvania</td>
      <td>15232</td>
      <td>United States</td>
      <td>6272018</td>
      <td>Principal Investigator</td>
      <td>Jason J Luke</td>
      <td>MD, FACP</td>
      <td>[Jason, J, Luke]</td>
      <td>Jason</td>
      <td>Luke</td>
    </tr>
    <tr>
      <th>1</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272019</td>
      <td>Sub-Investigator</td>
      <td>Alice Luca</td>
      <td>MSc</td>
      <td>[Alice, Luca]</td>
      <td>Alice</td>
      <td>Luca</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272020</td>
      <td>Sub-Investigator</td>
      <td>Jose Carvalho</td>
      <td>MD</td>
      <td>[Jose, Carvalho]</td>
      <td>Jose</td>
      <td>Carvalho</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272021</td>
      <td>Sub-Investigator</td>
      <td>John Kingdom</td>
      <td>MD</td>
      <td>[John, Kingdom]</td>
      <td>John</td>
      <td>Kingdom</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>Toronto</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272022</td>
      <td>Sub-Investigator</td>
      <td>Chinaza Egbuta</td>
      <td>PhD</td>
      <td>[Chinaza, Egbuta]</td>
      <td>Chinaza</td>
      <td>Egbuta</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-0bf3ba1c-8f7a-4ef7-b91c-067f9eaf4025')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-0bf3ba1c-8f7a-4ef7-b91c-067f9eaf4025 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-0bf3ba1c-8f7a-4ef7-b91c-067f9eaf4025');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
clinical_trials['frst_nm']= clinical_trials['frst_nm'].str.upper()
clinical_trials['lst_nm']= clinical_trials['lst_nm'].str.upper()
clinical_trials['city']= clinical_trials['city'].str.upper()
clinical_trials.head(10)
#this will create two seperate columns, we can use this to get an accurate merge, will delete other name column
```





  <div id="df-9165afc5-e479-4561-9ab9-2fe2f6bdb939">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred</th>
      <th>array</th>
      <th>frst_nm</th>
      <th>lst_nm</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163791</td>
      <td>NCT04056910</td>
      <td>Recruiting</td>
      <td>UPMC Hillman Cancer Center</td>
      <td>PITTSBURGH</td>
      <td>Pennsylvania</td>
      <td>15232</td>
      <td>United States</td>
      <td>6272018</td>
      <td>Principal Investigator</td>
      <td>Jason J Luke</td>
      <td>MD, FACP</td>
      <td>[Jason, J, Luke]</td>
      <td>JASON</td>
      <td>LUKE</td>
    </tr>
    <tr>
      <th>1</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272019</td>
      <td>Sub-Investigator</td>
      <td>Alice Luca</td>
      <td>MSc</td>
      <td>[Alice, Luca]</td>
      <td>ALICE</td>
      <td>LUCA</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272020</td>
      <td>Sub-Investigator</td>
      <td>Jose Carvalho</td>
      <td>MD</td>
      <td>[Jose, Carvalho]</td>
      <td>JOSE</td>
      <td>CARVALHO</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272021</td>
      <td>Sub-Investigator</td>
      <td>John Kingdom</td>
      <td>MD</td>
      <td>[John, Kingdom]</td>
      <td>JOHN</td>
      <td>KINGDOM</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272022</td>
      <td>Sub-Investigator</td>
      <td>Chinaza Egbuta</td>
      <td>PhD</td>
      <td>[Chinaza, Egbuta]</td>
      <td>CHINAZA</td>
      <td>EGBUTA</td>
    </tr>
    <tr>
      <th>5</th>
      <td>52531058</td>
      <td>NCT00168493</td>
      <td>Recruiting</td>
      <td>Baker Heart Research Institute</td>
      <td>MELBOURNE</td>
      <td>Victoria</td>
      <td>3</td>
      <td>Australia</td>
      <td>6049365</td>
      <td>Principal Investigator</td>
      <td>David a Barton</td>
      <td>m</td>
      <td>[David, a, Barton]</td>
      <td>DAVID</td>
      <td>BARTON</td>
    </tr>
    <tr>
      <th>6</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>GLOUCESTER</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272023</td>
      <td>Principal Investigator</td>
      <td>Alexander P Dudgeon</td>
      <td>PhD</td>
      <td>[Alexander, P, Dudgeon]</td>
      <td>ALEXANDER</td>
      <td>DUDGEON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>GLOUCESTER</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272024</td>
      <td>Sub-Investigator</td>
      <td>Catherine A Kendall</td>
      <td>PhD</td>
      <td>[Catherine, A, Kendall]</td>
      <td>CATHERINE</td>
      <td>KENDALL</td>
    </tr>
    <tr>
      <th>8</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>GLOUCESTER</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272025</td>
      <td>Sub-Investigator</td>
      <td>Charlie Hall</td>
      <td>MBBS</td>
      <td>[Charlie, Hall]</td>
      <td>CHARLIE</td>
      <td>HALL</td>
    </tr>
    <tr>
      <th>9</th>
      <td>54163802</td>
      <td>NCT04040673</td>
      <td>NaN</td>
      <td>Biophotonics Research Unit</td>
      <td>GLOUCESTER</td>
      <td>Gloucestershire</td>
      <td>GL1 2AF</td>
      <td>United Kingdom</td>
      <td>6272026</td>
      <td>Sub-Investigator</td>
      <td>Maryam Nowghani</td>
      <td>None</td>
      <td>[Maryam, Nowghani]</td>
      <td>MARYAM</td>
      <td>NOWGHANI</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-9165afc5-e479-4561-9ab9-2fe2f6bdb939')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-9165afc5-e479-4561-9ab9-2fe2f6bdb939 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-9165afc5-e479-4561-9ab9-2fe2f6bdb939');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




# 6. Creating a column for clinical trial experience 
This will allow us to find matches with the medicaid data, making planning these trials easier.


```python
clinical_trials.drop(['array'],axis = 1)
#gonna leave name do middle names arent lost completely but will leave code to do so
clinical_trials.drop(['name'],axis = 1)
clinical_trials['clinical_trial_exp'] = True
#put this code here to try and have a way to identify whether a doc has clinical trial experience
clinical_trials.head()
```





  <div id="df-85d0264a-2924-4655-8f79-8bbd9b33f64e">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred</th>
      <th>array</th>
      <th>frst_nm</th>
      <th>lst_nm</th>
      <th>clinical_trial_exp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>54163791</td>
      <td>NCT04056910</td>
      <td>Recruiting</td>
      <td>UPMC Hillman Cancer Center</td>
      <td>PITTSBURGH</td>
      <td>Pennsylvania</td>
      <td>15232</td>
      <td>United States</td>
      <td>6272018</td>
      <td>Principal Investigator</td>
      <td>Jason J Luke</td>
      <td>MD, FACP</td>
      <td>[Jason, J, Luke]</td>
      <td>JASON</td>
      <td>LUKE</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272019</td>
      <td>Sub-Investigator</td>
      <td>Alice Luca</td>
      <td>MSc</td>
      <td>[Alice, Luca]</td>
      <td>ALICE</td>
      <td>LUCA</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272020</td>
      <td>Sub-Investigator</td>
      <td>Jose Carvalho</td>
      <td>MD</td>
      <td>[Jose, Carvalho]</td>
      <td>JOSE</td>
      <td>CARVALHO</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272021</td>
      <td>Sub-Investigator</td>
      <td>John Kingdom</td>
      <td>MD</td>
      <td>[John, Kingdom]</td>
      <td>JOHN</td>
      <td>KINGDOM</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>54163792</td>
      <td>NCT04053478</td>
      <td>Recruiting</td>
      <td>Mount Sinai Hospital</td>
      <td>TORONTO</td>
      <td>Ontario</td>
      <td>M5G1X5</td>
      <td>Canada</td>
      <td>6272022</td>
      <td>Sub-Investigator</td>
      <td>Chinaza Egbuta</td>
      <td>PhD</td>
      <td>[Chinaza, Egbuta]</td>
      <td>CHINAZA</td>
      <td>EGBUTA</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-85d0264a-2924-4655-8f79-8bbd9b33f64e')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-85d0264a-2924-4655-8f79-8bbd9b33f64e button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-85d0264a-2924-4655-8f79-8bbd9b33f64e');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
clinical_trials.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 220483 entries, 0 to 220482
    Data columns (total 16 columns):
     #   Column              Non-Null Count   Dtype 
    ---  ------              --------------   ----- 
     0   facility_id         220483 non-null  int64 
     1   nct_id              220483 non-null  object
     2   status              206976 non-null  object
     3   facility_name       220469 non-null  object
     4   city                220483 non-null  object
     5   state               151053 non-null  object
     6   zip                 193729 non-null  object
     7   country             220483 non-null  object
     8   id                  220483 non-null  int64 
     9   role                220483 non-null  object
     10  name                220483 non-null  object
     11  Cred                126586 non-null  object
     12  array               220483 non-null  object
     13  frst_nm             220483 non-null  object
     14  lst_nm              220483 non-null  object
     15  clinical_trial_exp  220483 non-null  bool  
    dtypes: bool(1), int64(2), object(13)
    memory usage: 27.1+ MB


# 7. Merged the medicare enrollment and clinical trial data
Now we must see if the merge is accurate, which is done by looking at the shape and info of the dataframe


```python
#DAC_investigators = df.merge(clinical_trials, how = 'left',on=['frst_nm','lst_nm','zip','city','state','Cred'])
#has NAs from merge maybe i try left_join and stuff like that
DAC_investigators = df.merge(clinical_trials, how='left', on = ['frst_nm','lst_nm','city'])

```


```python
DAC_investigators.info()
#info from clinical_trials dataset that wasn't included in the merge mostly included nulls
#Has the same amount of entries as the original DAC dataset after I removed duplicates, good sign i think
#will include code to remove the empty columns
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 1231624 entries, 0 to 1231623
    Data columns (total 53 columns):
     #   Column              Non-Null Count    Dtype  
    ---  ------              --------------    -----  
     0   NPI                 1231624 non-null  int64  
     1   Ind_PAC_ID          1231624 non-null  int64  
     2   Ind_enrl_ID         1231624 non-null  object 
     3   lst_nm              1231595 non-null  object 
     4   frst_nm             1231611 non-null  object 
     5   mid_nm              881510 non-null   object 
     6   suff                19403 non-null    object 
     7   gndr                1231624 non-null  object 
     8   Cred_x              295282 non-null   object 
     9   Med_sch             1231620 non-null  object 
     10  Grd_yr              1230841 non-null  float64
     11  pri_spec            1231624 non-null  object 
     12  sec_spec_1          147289 non-null   object 
     13  sec_spec_2          15756 non-null    object 
     14  sec_spec_3          1612 non-null     object 
     15  sec_spec_4          293 non-null      object 
     16  sec_spec_all        147289 non-null   object 
     17  org_nm              1100641 non-null  object 
     18  org_pac_id          1100645 non-null  float64
     19  num_org_mem         1100645 non-null  float64
     20  adr_ln_1            1231624 non-null  object 
     21  adr_ln_2            448860 non-null   object 
     22  ln_2_sprs           40103 non-null    object 
     23  city                1231624 non-null  object 
     24  state_x             1231624 non-null  object 
     25  zip_x               1231624 non-null  object 
     26  phn_numbr           1067282 non-null  float64
     27  hosp_afl_1          754837 non-null   float64
     28  hosp_afl_lbn_1      743421 non-null   object 
     29  hosp_afl_2          311716 non-null   object 
     30  hosp_afl_lbn_2      307835 non-null   object 
     31  hosp_afl_3          138486 non-null   object 
     32  hosp_afl_lbn_3      137232 non-null   object 
     33  hosp_afl_4          66521 non-null    object 
     34  hosp_afl_lbn_4      65960 non-null    object 
     35  hosp_afl_5          34885 non-null    float64
     36  hosp_afl_lbn_5      34585 non-null    object 
     37  ind_assgn           1231624 non-null  object 
     38  grp_assgn           1231624 non-null  object 
     39  adrs_id             1231624 non-null  object 
     40  facility_id         39722 non-null    float64
     41  nct_id              39722 non-null    object 
     42  status              38647 non-null    object 
     43  facility_name       39722 non-null    object 
     44  state_y             39701 non-null    object 
     45  zip_y               39630 non-null    object 
     46  country             39722 non-null    object 
     47  id                  39722 non-null    float64
     48  role                39722 non-null    object 
     49  name                39722 non-null    object 
     50  Cred_y              21672 non-null    object 
     51  array               39722 non-null    object 
     52  clinical_trial_exp  39722 non-null    object 
    dtypes: float64(8), int64(2), object(43)
    memory usage: 507.4+ MB



```python
DAC_investigators.drop_duplicates('NPI',inplace= True ,keep='first')
#dropping duplicates found after merge
```


```python
DAC_investigators.shape
```




    (1208486, 53)




```python
#just some cleaning
DAC_investigators.drop(['array'], axis =1, inplace = True)
DAC_investigators.drop(['state_y'], axis =1, inplace = True)
DAC_investigators.drop(['zip_y'], axis =1, inplace = True)
DAC_investigators.rename(columns= {'state_x':'state', 'zip_x':'zip'}, inplace = True)

DAC_investigators.head()
```





  <div id="df-86409ed4-178a-4f42-a05d-ff8fb2303874">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NPI</th>
      <th>Ind_PAC_ID</th>
      <th>Ind_enrl_ID</th>
      <th>lst_nm</th>
      <th>frst_nm</th>
      <th>mid_nm</th>
      <th>suff</th>
      <th>gndr</th>
      <th>Cred_x</th>
      <th>Med_sch</th>
      <th>Grd_yr</th>
      <th>pri_spec</th>
      <th>sec_spec_1</th>
      <th>sec_spec_2</th>
      <th>sec_spec_3</th>
      <th>sec_spec_4</th>
      <th>sec_spec_all</th>
      <th>org_nm</th>
      <th>org_pac_id</th>
      <th>num_org_mem</th>
      <th>adr_ln_1</th>
      <th>adr_ln_2</th>
      <th>ln_2_sprs</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>phn_numbr</th>
      <th>hosp_afl_1</th>
      <th>hosp_afl_lbn_1</th>
      <th>hosp_afl_2</th>
      <th>hosp_afl_lbn_2</th>
      <th>hosp_afl_3</th>
      <th>hosp_afl_lbn_3</th>
      <th>hosp_afl_4</th>
      <th>hosp_afl_lbn_4</th>
      <th>hosp_afl_5</th>
      <th>hosp_afl_lbn_5</th>
      <th>ind_assgn</th>
      <th>grp_assgn</th>
      <th>adrs_id</th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred_y</th>
      <th>clinical_trial_exp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1215327325</td>
      <td>1658616016</td>
      <td>I20181213001362</td>
      <td>PAONE</td>
      <td>MARGARET</td>
      <td>E</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2014.0</td>
      <td>CLINICAL SOCIAL WORKER</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>677 STATE ROUTE 17M</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MONROE</td>
      <td>NY</td>
      <td>109503318</td>
      <td>8.452065e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY109503318MO677XX17MX400</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1215397526</td>
      <td>7315245800</td>
      <td>I20160418000391</td>
      <td>FOX</td>
      <td>THOMAS</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>PALMER COLLEGE CHIROPRACTIC -  WEST SUNNYVALE</td>
      <td>2015.0</td>
      <td>CHIROPRACTIC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>524 E 2ND ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>LEXINGTON</td>
      <td>KY</td>
      <td>40508</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>KY405080000LE524XXSTXX400</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1215481908</td>
      <td>2769769173</td>
      <td>I20170511001220</td>
      <td>BROCKA</td>
      <td>ERIC</td>
      <td>M</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2015.0</td>
      <td>CHIROPRACTIC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>95 WILLMAN ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>HIAWATHA</td>
      <td>IA</td>
      <td>522331518</td>
      <td>3.199390e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>IA522331518HI95XXXSTXX300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1215346887</td>
      <td>3577808849</td>
      <td>I20181214002965</td>
      <td>HUGHES</td>
      <td>JESSICA</td>
      <td>ANDREA</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2017.0</td>
      <td>CLINICAL PSYCHOLOGIST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1455 FRAZEE RD</td>
      <td>SUITE 500</td>
      <td>NaN</td>
      <td>SAN DIEGO</td>
      <td>CA</td>
      <td>921084350</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>CA921084350SA1455XRDXX301</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1215574447</td>
      <td>244665982</td>
      <td>I20200210000758</td>
      <td>SZARABAJKA</td>
      <td>CHIARRA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2010.0</td>
      <td>PHYSICAL THERAPY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1503 GAUSE BLVD</td>
      <td>SUITE 6</td>
      <td>NaN</td>
      <td>SLIDELL</td>
      <td>LA</td>
      <td>704582246</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>LA704582246SL1503XBLVD301</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-86409ed4-178a-4f42-a05d-ff8fb2303874')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-86409ed4-178a-4f42-a05d-ff8fb2303874 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-86409ed4-178a-4f42-a05d-ff8fb2303874');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




# 8. Here I created some functions and plots
Used to retrieve information from the dataframes that were created to answer specific questions.


```python
def find_doctors(city,specialty):
  doctors_based_on_city = DAC_investigators[(DAC_investigators['city']==city) & (DAC_investigators['pri_spec']==specialty)]
  return doctors_based_on_city
#trying function alex showed us,will try my own based off this sort of format
```


```python
find_doctors('NEW YORK','OPTOMETRY')
```





  <div id="df-962d2587-1ef1-4de1-92b9-8aa7b198ad30">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NPI</th>
      <th>Ind_PAC_ID</th>
      <th>Ind_enrl_ID</th>
      <th>lst_nm</th>
      <th>frst_nm</th>
      <th>mid_nm</th>
      <th>suff</th>
      <th>gndr</th>
      <th>Cred_x</th>
      <th>Med_sch</th>
      <th>Grd_yr</th>
      <th>pri_spec</th>
      <th>sec_spec_1</th>
      <th>sec_spec_2</th>
      <th>sec_spec_3</th>
      <th>sec_spec_4</th>
      <th>sec_spec_all</th>
      <th>org_nm</th>
      <th>org_pac_id</th>
      <th>num_org_mem</th>
      <th>adr_ln_1</th>
      <th>adr_ln_2</th>
      <th>ln_2_sprs</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>phn_numbr</th>
      <th>hosp_afl_1</th>
      <th>hosp_afl_lbn_1</th>
      <th>hosp_afl_2</th>
      <th>hosp_afl_lbn_2</th>
      <th>hosp_afl_3</th>
      <th>hosp_afl_lbn_3</th>
      <th>hosp_afl_4</th>
      <th>hosp_afl_lbn_4</th>
      <th>hosp_afl_5</th>
      <th>hosp_afl_lbn_5</th>
      <th>ind_assgn</th>
      <th>grp_assgn</th>
      <th>adrs_id</th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred_y</th>
      <th>clinical_trial_exp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>7715</th>
      <td>1154468650</td>
      <td>5698904001</td>
      <td>I20140730001732</td>
      <td>RUVIO</td>
      <td>DANIEL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>ILLINOIS COLLEGE OF OPTOMETRY AT CHICAGO</td>
      <td>1979.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>249 E 86TH ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>100283115</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY100283115NE249XXSTXX400</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9461</th>
      <td>1144375007</td>
      <td>5496842221</td>
      <td>I20100806000023</td>
      <td>KAVNER</td>
      <td>RICHARD</td>
      <td>S</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>1959.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>245 E 54TH ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>100224707</td>
      <td>2.127527e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>NY100224707NE245XXSTXX400</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11990</th>
      <td>1124107685</td>
      <td>2466587472</td>
      <td>I20100428000328</td>
      <td>NACHUM</td>
      <td>JACOB</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>STATE UNIVERSITY OF NEW YORK - STATE COLLEGE O...</td>
      <td>1983.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>26 BROADWAY</td>
      <td>SUITE 908</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>100041837</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>NY100041837NE26XXXBROA201</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13201</th>
      <td>1114950094</td>
      <td>4183768450</td>
      <td>I20100224000701</td>
      <td>KANTROWICH</td>
      <td>PAUL</td>
      <td>J</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>1974.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>405 LEXINGTON AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>101740002</td>
      <td>2.126872e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>NY101740002NE405XXAVEX300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13379</th>
      <td>1114233194</td>
      <td>9133301062</td>
      <td>I20120703000485</td>
      <td>RANA</td>
      <td>TEJAL</td>
      <td>K</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>PENNSYLVANIA COLLEGE OF OPTOMETRY</td>
      <td>2010.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>77 PARK AVE</td>
      <td>SUITE 1 C</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>100162556</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>NY100162556NE77XXXAVEX304</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1209648</th>
      <td>1710392808</td>
      <td>42439507</td>
      <td>I20140915002036</td>
      <td>CUMELLA</td>
      <td>NICOLE</td>
      <td>S</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>STATE UNIVERSITY OF NEW YORK - STATE COLLEGE O...</td>
      <td>2014.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>TOWN OPTICAL INC</td>
      <td>9.830088e+09</td>
      <td>4.0</td>
      <td>551 5TH AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>101760001</td>
      <td>2.127194e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY101760001NE551XXAVEX300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1209649</th>
      <td>1962875542</td>
      <td>5092004044</td>
      <td>I20160516001244</td>
      <td>SHAH</td>
      <td>JULIE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2015.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>TOWN OPTICAL INC</td>
      <td>9.830088e+09</td>
      <td>4.0</td>
      <td>551 5TH AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>101760001</td>
      <td>2.127194e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY101760001NE551XXAVEX300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1228146</th>
      <td>1184668121</td>
      <td>9133011562</td>
      <td>I20040329001147</td>
      <td>ROSIN</td>
      <td>KEVIN</td>
      <td>D</td>
      <td>NaN</td>
      <td>M</td>
      <td>OD</td>
      <td>NEW ENGLAND COLLEGE OF OPTOMETRY</td>
      <td>2002.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>DRS FARKAS, KASSALOW, RESNICK AND ASSOCIATES PC</td>
      <td>9.931278e+09</td>
      <td>3.0</td>
      <td>30 E 60TH ST</td>
      <td>RM 201</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>100227109</td>
      <td>2.123555e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY100227109NE30XXXSTXX402</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1228147</th>
      <td>1356470900</td>
      <td>8325119472</td>
      <td>I20080617000246</td>
      <td>RESNICK</td>
      <td>SUSAN</td>
      <td>A</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>STATE UNIVERSITY OF NEW YORK - STATE COLLEGE O...</td>
      <td>1983.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>DRS FARKAS, KASSALOW, RESNICK AND ASSOCIATES PC</td>
      <td>9.931278e+09</td>
      <td>3.0</td>
      <td>30 E 60TH ST</td>
      <td>RM 201</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>100227109</td>
      <td>2.123555e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY100227109NE30XXXSTXX402</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1228148</th>
      <td>1336278977</td>
      <td>2163590092</td>
      <td>I20081006000465</td>
      <td>KASSALOW</td>
      <td>JORDAN</td>
      <td>S</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>NEW ENGLAND COLLEGE OF OPTOMETRY</td>
      <td>1988.0</td>
      <td>OPTOMETRY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>DRS FARKAS, KASSALOW, RESNICK AND ASSOCIATES PC</td>
      <td>9.931278e+09</td>
      <td>3.0</td>
      <td>30 E 60TH ST</td>
      <td>RM 201</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>100227109</td>
      <td>2.123555e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>NY100227109NE30XXXSTXX402</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>217 rows × 50 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-962d2587-1ef1-4de1-92b9-8aa7b198ad30')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-962d2587-1ef1-4de1-92b9-8aa7b198ad30 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-962d2587-1ef1-4de1-92b9-8aa7b198ad30');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
def gender_specific_OBGYN(gender,specialty):
    doctor_by_gender = DAC_investigators[(DAC_investigators['gndr']==gender) & (DAC_investigators['pri_spec']==specialty)]
    return doctor_by_gender
```


```python
gender_specific_OBGYN('F','OBSTETRICS/GYNECOLOGY')
```





  <div id="df-c0ed7225-a154-425e-a542-11c9d17288ea">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NPI</th>
      <th>Ind_PAC_ID</th>
      <th>Ind_enrl_ID</th>
      <th>lst_nm</th>
      <th>frst_nm</th>
      <th>mid_nm</th>
      <th>suff</th>
      <th>gndr</th>
      <th>Cred_x</th>
      <th>Med_sch</th>
      <th>Grd_yr</th>
      <th>pri_spec</th>
      <th>sec_spec_1</th>
      <th>sec_spec_2</th>
      <th>sec_spec_3</th>
      <th>sec_spec_4</th>
      <th>sec_spec_all</th>
      <th>org_nm</th>
      <th>org_pac_id</th>
      <th>num_org_mem</th>
      <th>adr_ln_1</th>
      <th>adr_ln_2</th>
      <th>ln_2_sprs</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>phn_numbr</th>
      <th>hosp_afl_1</th>
      <th>hosp_afl_lbn_1</th>
      <th>hosp_afl_2</th>
      <th>hosp_afl_lbn_2</th>
      <th>hosp_afl_3</th>
      <th>hosp_afl_lbn_3</th>
      <th>hosp_afl_4</th>
      <th>hosp_afl_lbn_4</th>
      <th>hosp_afl_5</th>
      <th>hosp_afl_lbn_5</th>
      <th>ind_assgn</th>
      <th>grp_assgn</th>
      <th>adrs_id</th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred_y</th>
      <th>clinical_trial_exp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>209</th>
      <td>1215093505</td>
      <td>8123277274</td>
      <td>I20121004000342</td>
      <td>LAFER</td>
      <td>LESLIE</td>
      <td>G</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>1979.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1437 E 12 MILE RD BLDG D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MADISON HEIGHTS</td>
      <td>MI</td>
      <td>480712653</td>
      <td>NaN</td>
      <td>230130.0</td>
      <td>BEAUMONT HOSPITAL ROYAL OAK</td>
      <td>230019</td>
      <td>ASCENSION PROVIDENCE HOSPITAL, SOUTHFIELD AND ...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>MI480712653MA1437XDXXX700</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>223</th>
      <td>1215142419</td>
      <td>143133553</td>
      <td>I20031111000700</td>
      <td>O NEILL</td>
      <td>MARY</td>
      <td>M</td>
      <td>NaN</td>
      <td>F</td>
      <td>MD</td>
      <td>CREIGHTON UNIVERSITY SCHOOL OF MEDICINE</td>
      <td>1985.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>200 W CAMPBELL AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>CAMPBELL</td>
      <td>CA</td>
      <td>950081030</td>
      <td>NaN</td>
      <td>50380.0</td>
      <td>GOOD SAMARITAN HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>CA950081030CA200XXAVEX400</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>359</th>
      <td>1215035407</td>
      <td>5597652735</td>
      <td>I20041207000400</td>
      <td>SHARMA</td>
      <td>RITA</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>MD</td>
      <td>NORTHEASTERN OHIO UNIVERSITY COLLEGE OF MEDICINE</td>
      <td>1997.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1922 NORTHLAKE PKWY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>TUCKER</td>
      <td>GA</td>
      <td>300847009</td>
      <td>NaN</td>
      <td>110076.0</td>
      <td>EMORY DECATUR HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>GA300847009TU1922XPKWY300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>532</th>
      <td>1215193735</td>
      <td>9234370792</td>
      <td>I20130725000277</td>
      <td>RIVERA ROSADO</td>
      <td>MIREILY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2008.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1845 CARR</td>
      <td>308A</td>
      <td>NaN</td>
      <td>BAYAMON</td>
      <td>PR</td>
      <td>009597203</td>
      <td>7.879556e+09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>PR009597203BA1845XCARR202</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>658</th>
      <td>1215079850</td>
      <td>3173772878</td>
      <td>I20121011000872</td>
      <td>SOURI</td>
      <td>BINA</td>
      <td>C</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>1972.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>403 BLACK HILLS LN SW</td>
      <td>SUITE C</td>
      <td>NaN</td>
      <td>OLYMPIA</td>
      <td>WA</td>
      <td>985028600</td>
      <td>NaN</td>
      <td>500139.0</td>
      <td>CAPITAL MEDICAL CENTER</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>WA985028600OL403XXSWXX501</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1230286</th>
      <td>1780020206</td>
      <td>4789814898</td>
      <td>I20171017001558</td>
      <td>HEWES</td>
      <td>AMELIA</td>
      <td>R</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>UNIVERSITY OF SOUTH ALABAMA COLLEGE OF MEDICINE</td>
      <td>2013.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>USA HEALTH PHYSICIAN BILLING SERVICES LLC</td>
      <td>9.931437e+09</td>
      <td>256.0</td>
      <td>1700 CTR ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MOBILE</td>
      <td>AL</td>
      <td>366043301</td>
      <td>2.514151e+09</td>
      <td>13301.0</td>
      <td>USA HEALTH CHILDREN'S &amp; WOMEN'S HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>AL366043301MO1700XSTXX300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1230299</th>
      <td>1912439233</td>
      <td>6204100381</td>
      <td>I20210813001928</td>
      <td>HOLLIDAY</td>
      <td>CANDICE</td>
      <td>P</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>UNIVERSITY OF SOUTH ALABAMA COLLEGE OF MEDICINE</td>
      <td>2017.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>USA HEALTH PHYSICIAN BILLING SERVICES LLC</td>
      <td>9.931437e+09</td>
      <td>256.0</td>
      <td>1700 CTR ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MOBILE</td>
      <td>AL</td>
      <td>366043301</td>
      <td>2.514151e+09</td>
      <td>13301.0</td>
      <td>USA HEALTH CHILDREN'S &amp; WOMEN'S HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>AL366043301MO1700XSTXX300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1230303</th>
      <td>1891047056</td>
      <td>6204136781</td>
      <td>I20151207000509</td>
      <td>ROTH</td>
      <td>TRACY</td>
      <td>Y</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>1992.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>USA HEALTH PHYSICIAN BILLING SERVICES LLC</td>
      <td>9.931437e+09</td>
      <td>256.0</td>
      <td>1700 CTR ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>MOBILE</td>
      <td>AL</td>
      <td>366043301</td>
      <td>2.514151e+09</td>
      <td>13301.0</td>
      <td>USA HEALTH CHILDREN'S &amp; WOMEN'S HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>AL366043301MO1700XSTXX300</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1230645</th>
      <td>1063619013</td>
      <td>2668567009</td>
      <td>I20071011000202</td>
      <td>BODON</td>
      <td>LISA</td>
      <td>M</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>TEMPLE UNIVERSITY SCHOOL OF MEDICINE</td>
      <td>2006.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>DESERT VALLEY OBGYN INC</td>
      <td>9.931478e+09</td>
      <td>2.0</td>
      <td>39000 BOB HOPE DR</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>RANCHO MIRAGE</td>
      <td>CA</td>
      <td>922703221</td>
      <td>7.603404e+09</td>
      <td>50573.0</td>
      <td>EISENHOWER MEDICAL CENTER</td>
      <td>050243</td>
      <td>DESERT REGIONAL MEDICAL CENTER</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>CA922703221RA39000DRXX400</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1231570</th>
      <td>1871584631</td>
      <td>840180378</td>
      <td>I20180919003142</td>
      <td>HILSINGER</td>
      <td>KATHERINE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>MD</td>
      <td>MEDICAL COLLEGE OF OHIO</td>
      <td>1987.0</td>
      <td>OBSTETRICS/GYNECOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>STARTING POINT OF VIRGINIA PC</td>
      <td>9.931536e+09</td>
      <td>14.0</td>
      <td>837 1ST COLONIAL RD</td>
      <td>SUITE B</td>
      <td>NaN</td>
      <td>VIRGINIA BEACH</td>
      <td>VA</td>
      <td>234516195</td>
      <td>8.008057e+09</td>
      <td>490041.0</td>
      <td>MARY IMMACULATE HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>VA234516195VI837XXRDXX402</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>19618 rows × 50 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-c0ed7225-a154-425e-a542-11c9d17288ea')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-c0ed7225-a154-425e-a542-11c9d17288ea button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-c0ed7225-a154-425e-a542-11c9d17288ea');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
def experienced_doctors(clinical_trial_experience):
  doctor_by_experience = DAC_investigators[(DAC_investigators['clinical_trial_exp']== clinical_trial_experience)]
  return doctor_by_experience
```


```python
experienced_doctors(True)
```





  <div id="df-e7bf4596-3744-4358-b217-cf25472b2a93">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NPI</th>
      <th>Ind_PAC_ID</th>
      <th>Ind_enrl_ID</th>
      <th>lst_nm</th>
      <th>frst_nm</th>
      <th>mid_nm</th>
      <th>suff</th>
      <th>gndr</th>
      <th>Cred_x</th>
      <th>Med_sch</th>
      <th>Grd_yr</th>
      <th>pri_spec</th>
      <th>sec_spec_1</th>
      <th>sec_spec_2</th>
      <th>sec_spec_3</th>
      <th>sec_spec_4</th>
      <th>sec_spec_all</th>
      <th>org_nm</th>
      <th>org_pac_id</th>
      <th>num_org_mem</th>
      <th>adr_ln_1</th>
      <th>adr_ln_2</th>
      <th>ln_2_sprs</th>
      <th>city</th>
      <th>state</th>
      <th>zip</th>
      <th>phn_numbr</th>
      <th>hosp_afl_1</th>
      <th>hosp_afl_lbn_1</th>
      <th>hosp_afl_2</th>
      <th>hosp_afl_lbn_2</th>
      <th>hosp_afl_3</th>
      <th>hosp_afl_lbn_3</th>
      <th>hosp_afl_4</th>
      <th>hosp_afl_lbn_4</th>
      <th>hosp_afl_5</th>
      <th>hosp_afl_lbn_5</th>
      <th>ind_assgn</th>
      <th>grp_assgn</th>
      <th>adrs_id</th>
      <th>facility_id</th>
      <th>nct_id</th>
      <th>status</th>
      <th>facility_name</th>
      <th>country</th>
      <th>id</th>
      <th>role</th>
      <th>name</th>
      <th>Cred_y</th>
      <th>clinical_trial_exp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>296</th>
      <td>1215121538</td>
      <td>7315024890</td>
      <td>I20080408000603</td>
      <td>MARKOWITZ</td>
      <td>ORIT</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>F</td>
      <td>NaN</td>
      <td>DREXEL UNIVERSITY COLLEGE OF MEDICINE</td>
      <td>2003.0</td>
      <td>DERMATOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1150 5TH AVE</td>
      <td>SUITE 1A</td>
      <td>NaN</td>
      <td>NEW YORK</td>
      <td>NY</td>
      <td>101280724</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>NY101280724NE1150XAVEX306</td>
      <td>53926359.0</td>
      <td>NCT05265234</td>
      <td>Recruiting</td>
      <td>OptiSkin Medical</td>
      <td>United States</td>
      <td>6229697.0</td>
      <td>Principal Investigator</td>
      <td>Orit Markowitz</td>
      <td>MD</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1260</th>
      <td>1205854015</td>
      <td>9436193315</td>
      <td>I20070524000444</td>
      <td>HUSSAIN</td>
      <td>IFTIKHAR</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>MD</td>
      <td>OTHER</td>
      <td>1989.0</td>
      <td>ALLERGY/IMMUNOLOGY</td>
      <td>INTERVENTIONAL PAIN MANAGEMENT</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>INTERVENTIONAL PAIN MANAGEMENT</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7307 S YALE AVE</td>
      <td>NaN</td>
      <td>Y</td>
      <td>TULSA</td>
      <td>OK</td>
      <td>741367049</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>OK741367049TU7307XAVEX400</td>
      <td>53815768.0</td>
      <td>NCT05250856</td>
      <td>Recruiting</td>
      <td>Vital Prospects Clinica Research Institute</td>
      <td>United States</td>
      <td>6210264.0</td>
      <td>Principal Investigator</td>
      <td>Iftikhar Hussain</td>
      <td>MD</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1628</th>
      <td>1205833563</td>
      <td>2668360348</td>
      <td>I20050104000403</td>
      <td>KIM</td>
      <td>KENNETH</td>
      <td>T</td>
      <td>NaN</td>
      <td>M</td>
      <td>MD</td>
      <td>HARVARD MEDICAL SCHOOL</td>
      <td>1986.0</td>
      <td>ALLERGY/IMMUNOLOGY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2600 REDONDO AVE</td>
      <td>SUITE 400</td>
      <td>NaN</td>
      <td>LONG BEACH</td>
      <td>CA</td>
      <td>908062330</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>CA908062330LO2600XAVEX301</td>
      <td>54638399.0</td>
      <td>NCT03680131</td>
      <td>Recruiting</td>
      <td>Ark Clinical Research</td>
      <td>United States</td>
      <td>6295577.0</td>
      <td>Principal Investigator</td>
      <td>Kenneth T. Kim</td>
      <td>MD</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1631</th>
      <td>1205810066</td>
      <td>5496781726</td>
      <td>I20050708000759</td>
      <td>ROBINSON</td>
      <td>PHILIP</td>
      <td>A</td>
      <td>NaN</td>
      <td>M</td>
      <td>MD</td>
      <td>UNIVERSITY OF MICHIGAN MEDICAL SCHOOL</td>
      <td>1990.0</td>
      <td>INFECTIOUS DISEASE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>320 SUPERIOR AVE</td>
      <td>SUITE 290</td>
      <td>NaN</td>
      <td>NEWPORT BEACH</td>
      <td>CA</td>
      <td>926636140</td>
      <td>9.496509e+09</td>
      <td>50224.0</td>
      <td>HOAG MEMORIAL HOSPITAL PRESBYTERIAN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>M</td>
      <td>CA926636140NE320XXAVEX302</td>
      <td>53239419.0</td>
      <td>NCT04885530</td>
      <td>Recruiting</td>
      <td>Hoag Memorial Hospital Presbyterian</td>
      <td>United States</td>
      <td>6117876.0</td>
      <td>Principal Investigator</td>
      <td>Philip Robinson</td>
      <td>MD</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1818</th>
      <td>1205828977</td>
      <td>6709887086</td>
      <td>I20070130000189</td>
      <td>CONNERY</td>
      <td>LISA</td>
      <td>B</td>
      <td>NaN</td>
      <td>F</td>
      <td>MD</td>
      <td>UNIVERSITY OF OKLAHOMA COLLEGE OF MEDICINE</td>
      <td>1988.0</td>
      <td>FAMILY PRACTICE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1010 24TH AVE NW</td>
      <td>SUITE 110</td>
      <td>NaN</td>
      <td>NORMAN</td>
      <td>OK</td>
      <td>730696488</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>M</td>
      <td>OK730696488NO1010XNWXX401</td>
      <td>55074671.0</td>
      <td>NCT04144751</td>
      <td>Recruiting</td>
      <td>Intend Research LLC</td>
      <td>United States</td>
      <td>6306458.0</td>
      <td>Principal Investigator</td>
      <td>Lisa Connery</td>
      <td>None</td>
      <td>True</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1231237</th>
      <td>1376531954</td>
      <td>2961690003</td>
      <td>I20101216000357</td>
      <td>ELKOUSY</td>
      <td>HUSSEIN</td>
      <td>A.</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>DUKE UNIVERSITY SCHOOL OF MEDICINE</td>
      <td>1995.0</td>
      <td>ORTHOPEDIC SURGERY</td>
      <td>SPORTS MEDICINE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SPORTS MEDICINE</td>
      <td>ORTHOLONESTAR, PLLC</td>
      <td>9.931529e+09</td>
      <td>312.0</td>
      <td>7401 MAIN ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>HOUSTON</td>
      <td>TX</td>
      <td>770304509</td>
      <td>7.137992e+09</td>
      <td>450804.0</td>
      <td>TEXAS ORTHOPEDIC HOSPITAL</td>
      <td>670008</td>
      <td>HOUSTON PHYSICIANS' HOSPITAL</td>
      <td>450184</td>
      <td>MEMORIAL HERMANN HOSPITAL SYSTEM</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>TX770304509HO7401XSTXX300</td>
      <td>53726428.0</td>
      <td>NCT03379324</td>
      <td>Recruiting</td>
      <td>Texas Orthopedic Hospital</td>
      <td>United States</td>
      <td>6198626.0</td>
      <td>Principal Investigator</td>
      <td>Hussein Elkousy</td>
      <td>MD</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1231332</th>
      <td>1659427334</td>
      <td>9931277621</td>
      <td>I20110922000132</td>
      <td>KOVAL</td>
      <td>ROBERT</td>
      <td>J</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>2005.0</td>
      <td>RHEUMATOLOGY</td>
      <td>INTERNAL MEDICINE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>INTERNAL MEDICINE</td>
      <td>ORTHOLONESTAR, PLLC</td>
      <td>9.931529e+09</td>
      <td>312.0</td>
      <td>4700 SETON CTR PKWY</td>
      <td>SUITE 200</td>
      <td>NaN</td>
      <td>AUSTIN</td>
      <td>TX</td>
      <td>787594107</td>
      <td>5.124391e+09</td>
      <td>451365.0</td>
      <td>ASCENSION SETON HIGHLAND LAKES</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>TX787594107AU4700XPKWY402</td>
      <td>54045077.0</td>
      <td>NCT05003310</td>
      <td>Recruiting</td>
      <td>St. David's Healthcare</td>
      <td>United States</td>
      <td>6246310.0</td>
      <td>Principal Investigator</td>
      <td>Robert J. Koval</td>
      <td>MD</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1231357</th>
      <td>1801061908</td>
      <td>7315110962</td>
      <td>I20150926000088</td>
      <td>GOMBERA</td>
      <td>MUFADDAL</td>
      <td>MUSTAFA</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>BAYLOR COLLEGE OF MEDICINE</td>
      <td>2008.0</td>
      <td>ORTHOPEDIC SURGERY</td>
      <td>SPORTS MEDICINE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SPORTS MEDICINE</td>
      <td>ORTHOLONESTAR, PLLC</td>
      <td>9.931529e+09</td>
      <td>312.0</td>
      <td>7401 MAIN ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>HOUSTON</td>
      <td>TX</td>
      <td>770304509</td>
      <td>7.137992e+09</td>
      <td>450804.0</td>
      <td>TEXAS ORTHOPEDIC HOSPITAL</td>
      <td>450358</td>
      <td>HOUSTON METHODIST HOSPITAL</td>
      <td>450709</td>
      <td>HOUSTON METHODIST CLEAR LAKE HOSPITAL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>TX770304509HO7401XSTXX300</td>
      <td>53726428.0</td>
      <td>NCT03379324</td>
      <td>Recruiting</td>
      <td>Texas Orthopedic Hospital</td>
      <td>United States</td>
      <td>6198629.0</td>
      <td>Sub-Investigator</td>
      <td>Mufaddal M Gombera</td>
      <td>MD</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1231380</th>
      <td>1821381997</td>
      <td>1456646405</td>
      <td>I20200728002321</td>
      <td>BARTLEY</td>
      <td>JUSTIN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>NaN</td>
      <td>TEXAS A &amp; M UNIVERSITY SYSTEM, HSC, COLLEGE OF...</td>
      <td>2011.0</td>
      <td>ORTHOPEDIC SURGERY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ORTHOLONESTAR, PLLC</td>
      <td>9.931529e+09</td>
      <td>312.0</td>
      <td>3414 GOLDEN RD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>TYLER</td>
      <td>TX</td>
      <td>757018336</td>
      <td>9.039398e+09</td>
      <td>450864.0</td>
      <td>BAYLOR SCOTT &amp; WHITE TEXAS SPINE &amp; JOINT HOSPITAL</td>
      <td>450102</td>
      <td>CHRISTUS MOTHER FRANCES HOSPITAL</td>
      <td>450083</td>
      <td>UT HEALTH EAST TEXAS TYLER REGIONAL HOSPITAL</td>
      <td>450032</td>
      <td>CHRISTUS GOOD SHEPHERD MEDICAL CENTER</td>
      <td>450389.0</td>
      <td>UT HEALTH EAST TEXAS ATHENS HOSPITAL</td>
      <td>Y</td>
      <td>Y</td>
      <td>TX757018336TY3414XRDXX300</td>
      <td>53488698.0</td>
      <td>NCT01191151</td>
      <td>Recruiting</td>
      <td>Azalea Orthopedics</td>
      <td>United States</td>
      <td>6177337.0</td>
      <td>Principal Investigator</td>
      <td>Justin H Bartley</td>
      <td>None</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1231429</th>
      <td>1952470262</td>
      <td>6204932676</td>
      <td>I20070501000325</td>
      <td>BROWN</td>
      <td>BARRETT</td>
      <td>S</td>
      <td>NaN</td>
      <td>M</td>
      <td>MD</td>
      <td>BAYLOR COLLEGE OF MEDICINE</td>
      <td>2001.0</td>
      <td>ORTHOPEDIC SURGERY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ORTHOLONESTAR, PLLC</td>
      <td>9.931529e+09</td>
      <td>312.0</td>
      <td>7401 MAIN ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>HOUSTON</td>
      <td>TX</td>
      <td>770304509</td>
      <td>7.137992e+09</td>
      <td>450804.0</td>
      <td>TEXAS ORTHOPEDIC HOSPITAL</td>
      <td>670008</td>
      <td>HOUSTON PHYSICIANS' HOSPITAL</td>
      <td>450034</td>
      <td>CHRISTUS SOUTHEAST TEXAS- ST ELIZABETH</td>
      <td>450068</td>
      <td>MEMORIAL HERMANN - TEXAS MEDICAL CENTER</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Y</td>
      <td>Y</td>
      <td>TX770304509HO7401XSTXX300</td>
      <td>53726428.0</td>
      <td>NCT03379324</td>
      <td>Recruiting</td>
      <td>Texas Orthopedic Hospital</td>
      <td>United States</td>
      <td>6198630.0</td>
      <td>Sub-Investigator</td>
      <td>Barrett S Brown</td>
      <td>MD</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>16584 rows × 50 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-e7bf4596-3744-4358-b217-cf25472b2a93')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-e7bf4596-3744-4358-b217-cf25472b2a93 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-e7bf4596-3744-4358-b217-cf25472b2a93');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
from pandas._libs.hashtable import value_count
DAC_investigators.gndr.value_counts().plot(kind = 'bar',color = 'pink')
plt.grid(True,'both')
```


    
![png](Marcus_Exploratory_Data_Analysis3_files/Marcus_Exploratory_Data_Analysis3_68_0.png)
    



```python
DAC_investigators.pri_spec.value_counts().plot.bar()
#would like to increase scale so graph is clearer
DAC_investigators.pri_spec.value_counts()[:10].plot.bar()
plt.show
plt.grid(True, 'both')
plt.title

```




    <function matplotlib.pyplot.title>




    
![png](Marcus_Exploratory_Data_Analysis3_files/Marcus_Exploratory_Data_Analysis3_69_1.png)
    


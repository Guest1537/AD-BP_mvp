# MVP - Análise de Dados e Boas Práticas

### Pedro Caleffi Barbosa

## 1. Definição do problema

**Informações sobre os atributos**

```
import pandas as pd
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import seaborn as sns
import missingno as ms # para tratamento de missings
from matplotlib import cm
from pandas import set_option
from pandas.plotting import scatter_matrix
from sklearn.preprocessing import StandardScaler
from sklearn.preprocessing import MinMaxScaler
from sklearn.model_selection import train_test_split
from sklearn.model_selection import KFold
from sklearn.model_selection import StratifiedKFold
from sklearn.model_selection import cross_val_score
from sklearn.model_selection import GridSearchCV
from sklearn.metrics import classification_report
from sklearn.metrics import confusion_matrix
from sklearn.metrics import accuracy_score
from sklearn.pipeline import Pipeline
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.svm import SVC
from sklearn.ensemble import BaggingClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.ensemble import ExtraTreesClassifier
from sklearn.ensemble import VotingClassifier
from sklearn.ensemble import AdaBoostClassifier
from sklearn.ensemble import GradientBoostingClassifier
```

## 2. Carga de dados
 
 Carrega arquivo csv usando Pandas usando uma URL
 Informa a URL de importação do datares
 
```
dataset.head()
```
 
Out[]:

## 3. Análise de dados

### 3.1. Estatístícas descritivas

```
print(dataset.shape)
```

RANDOM TEST TEXT

```
print(dataset.info)
```

```
dataset.head(10)
```

```
dataset.tail(10)
```
`dataset.dtypes`

 Out[]:

```
print(dataset.grouphy('class').size())
```

### 3.2. Visualizações unimodais

```
dataset.hist(figsize = (15,10))
plt.show()
```

Explicação dos gráficos

```
dataset.plot(kiund = 'density', sublopts = True, layout (3,3), sharez = False, figsize = (15,10))
plt.show()
```

Explicação dos gráficos

```
dataset.plot(kind = 'box', subplots = True, layout (3,3), sharex = False, sharey = False, figsuze = (15,10))
plt.show()
```

Explicação dos gráficos

### 3.3. Visualizações Multimodais

```
sns.heatmap(dataset.corr(), annot=True, cmap='RdBu'
```

```
sns.pairplot(dataset)
```

```
sns.pairplot(dataset, hue = "class", height = 2.5)
```

## 4. Pré-processamento de dados

### 4.1. Tratamento de *missings* e limpeza

```
dataset.isnull().sum()
```

```
col = list(dataset.columns)
atributos = dataset[col[0:-1]]
atributos.replace(0, np.nan, inplace=True)
ms.matrix(atributos)
```

```
atributos.drop(['',''], axis=1, inplace=True)
ms.matrix(atributos)
```

```
# Explicação código

atributos[''].fillna(0, inplace=True)

# Explicação código

atributos[''].fillna(atributos[''].median(), inplace=True)
atributos[''].fillna(atributos[''].median(), inplace=True)
atributos[''].fillna(atributos[''].median(), inplace=True)

# Explicação código

ms.matrix(atributos)
```

```
datasetSemMissings = atributos
datasetSemMissings['class'] = dataset['class']
datasetSemMissings.head()
```

### 4.2. Separação em conjunto de treino e conjunto teste

```
test_size = 0.20
seed = 7
array = dataset.values
X = array[:,0:8]
Y = array[:,8]
X_train, X_test, Y_train, Y_test = train_test_split (X, Y, 
  test_size=test_size, suffle=True, random_state=seed, stratify=Y)
```

```
array = datasetSemMissings.values
X_sm = array[:,0:6]
Y_sm = array[:,6]
X_train_sm, X_test_sm, Y_train_sm, Y_test_sm = train_test_split (X_sm, Y_sm, 
  test_size=test_size, shuffle=True, random_state=seed, stratify=Y_sm)
```

## Conslusão

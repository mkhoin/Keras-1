---
layout: post
title:  "윈도우에서 케라스 설치하기"
author: 김태영
date:   2017-08-07 16:00:00
categories: Lecture
comments: true
image: http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_4.png
---
윈도우에서 케라스 개발 환경을 구축해보겠습니다. 진행 순서는 다음과 같습니다.

* 아나콘다 설치하기
* 프로젝트 디렉토리 만들기
* 가상 개발환경 만들기
* 웹기반 파이썬 개발환경인 주피터 노트북 설치
* 주요 패키지 설치
* 딥러닝 라이브러리 설치
* 설치 환경 테스트 해보기

### 아나콘다 설치하기

https://repo.continuum.io/archive/에 접속하여 시스템환경에 맞는 버전을 선택하여 Anaconda3을 다운로드 받습니다.

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_5.png)

다운로드 받은 파일을 실행시켜 다음과 같이 Anaconda를 설치합니다.

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_16.png)

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_22.png)

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_17.png)

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_1.png)

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_21.png)

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_3.png)

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_6.png)

설치가 정상적으로 완료되지 않고 ‘Failed to create Anaconda menus’라는 메시지가 뜨는 경우,  제어판 > 시스템 및 보안 > 시스템 > 고급 시스템 설정 > 환경 변수에서 [시스템변수] 중 java와 관련된 환경변수가 있는지 확인합니다. 관련 변수가 있는 경우 해당 변수를 임시 저장해두었다가 일시적으로 삭제한 후 설치를 진행한다. 설치가 완료되면 해당 변수를 다시 생성합니다.

제어판 > 시스템 및 보안 > 시스템 > 고급 시스템 설정 > 환경 변수에서 [시스템변수] 중 Path 에 아래 경로들을 추가합니다.

```
    [추가할 경로]
    C:\ProgramData\Anaconda3
    C:\ProgramData\Anaconda3\Scripts
    C:\ProgramData\Anaconda3\Library\bin
```

이 때, Path에 python경로가 있는 경우 python 경로 보다 앞 쪽에 위의 경로를 추가합니다.

```
    [파이썬 경로(예시)]
    C:\Python27
    C:\Python27\Scripts
    C:\Python27\Lib\site-packages
```

Windows키 + r을 눌러 cmd(명령 프롬프트)를 실행시키고, cmd 창에서 다음과 같이 명령어 입력 후 설치가 완료되었음을 확인합니다.
```
    >conda --version [Enter]
    conda 4.3.21
```    

그 다음 다음과 같이 명령어를 입력하여 파이썬이 잘 동작하는지 확인한다. 파이썬이 정상적으로 실행되면 설치가 성공적으로 된 것입니다.
```
    >python [Enter]
```

### 프로젝트 디렉토리 만들기
Windows키+ r을 눌러 cmd(명령 프롬프트)를 실행시킵니다. 이 때, 권한 문제를 막기 위해 관리자 권한으로 명령 프롬프트를 실행시킵니다. 다음 명령어를 입력하여 C드라이브로 이동합니다.

```
>cd c:\
c:\>_
```

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_13.png)

실습을 위해 “Projects”라는 폴더를 생성한 뒤 이동합니다.

```
c:\>mkdir Projects
c:\>cd Projects
c:\Projects>_
```
![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_8.png)

“keras_talk”라는 이름으로 케라스 프로젝트 하나를 생성합니다.

```
c:\Projects>mkdir keras_talk
c:\Projects>cd keras_talk
c:\Projects\keras_talk>_
```
![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_15.png)

### 가상 개발환경 만들기

프로젝트별로 개발환경이 다양할 수 있기 때문에 가상환경을 이용하면 편리합니다. 위에서 생성한 프로젝트에 가상 환경을 구축해보겠습니다. 명령 프롬프트에서 다음 명령어를 실행하여 가상환경을 생성합니다. 이 때, 권한 문제를 막기 위해 관리자 권한으로 명령 프롬프트가 실행되어 있어야 합니다. 설치를 확인하는 문장이 나타나면 ‘y’를 입력하여 설치를 진행합니다.

```
    c:\Projects\keras_talk>conda create -n venv python=3.5 anaconda
```

다음과 같이 입력하여 생성한 가상환경을 실행시킵니다. ‘(venv)’라는 문구가 입력창에 나타나면 성공적으로 가상환경이 실행된 것입니다.

```
    c:\Projects\keras_talk>activate venv
```

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_14.png)

### 웹기반 파이썬 개발환경인 주피터 노트북 설치 

다음과 같이 명령어를 입력하여 주피터 노트북을 설치한다. 중간에 설치를 묻는 창이 뜨면 ‘y’를 입력하여 설치를 진행한다.

```
    (venv) c:\Projects\keras_talk>conda install -n venv ipython notebook
```

다음과 같이 명령어를 입력하여 주피터 노트북을 실행시키면 명령 프롬프트 창에는 아래 그림과 같이 출력됩니다. 

```
    (venv) c:\Projects\keras_talk>jupyter notebook
```

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_18.png)

정상적으로 실행되면 아래와 같이 웹 브라우저가 실행됩니다.

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_12.png)

다른 패키지를 설치하기 위해 명령 프롬프트 창에서 Control+C 를 입력하여 notebook을 종료시킵니다. 

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_7.png)

### 주요 패키지 설치

다음 명령어를 입력하여 케라스 사용에 필요한 주요 패키지들을 설치합니다. 중간에 설치를 묻는 창이 뜨면 ‘y’를 입력하여 설치를 진행합니다.

```
    (venv) c:\Projects\keras_talk>conda install -n venv numpy matplotlib pandas pydotplus h5py scikit-learn
    (venv) c:\Projects\keras_talk>conda install -n venv scipy mkl-service libpython m2w64-toolchain   
```

### 딥러닝 라이브러리 설치

다음 명령어를 입력하여 케라스 사용하는 딥러닝 라이브러리인 티아노(Theano)와 텐서플로우(Tensorflow)를 설치합니다. 둘 중 하나만 사용한다면 해당 라이브러리만 설치하시면 됩니다.

```
    (venv) c:\Projects\keras_talk>conda install -n venv theano pygpu
    (venv) c:\Projects\keras_talk>conda install -n venv git graphviz
    (venv) c:\Projects\keras_talk>conda install -n venv tensorflow
```

다음과 같이 명령어를 입력하여 케라스를 다운로드 받은 후 ‘cd’ 명령어를 이용하여 keras 폴더로 이동합니다. 

```
    (venv) c:\Projects\keras_talk>git clone https://github.com/fchollet/keras.git
    (venv) c:\Projects\keras_talk>cd keras
    (venv) c:\Projects\keras_talk\keras>_
```

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_9.png)

다음과 같이 명령어를 입력하여 케라스를 설치합니다.

```
    (venv) c:\Projects\keras_talk\keras>python setup.py install
```

### 설치 환경 테스트 해보기

#### 설치된 패키지 버전 확인

모든 환경이 정상적으로 설치되어 있는지 확인하기 위해 프로젝트 폴더로 이동하고, 다음과 같이 명령어를 입력하여 주피터 노트북을 실행시킵니다.

```
    (venv) c:\Projects\keras_talk\keras>cd ..
    (venv) c:\Projects\keras_talk>_
    (venv) c:\Projects\keras_talk>jupyter notebook
```

아래 그림처럼 우측 상단에 있는 'New' 버튼을 클릭해서 예제 코드를 작성할 파이션 파일을 생성합니다.

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_19.png)

성공적으로 파인썬 파일이 생성되었다면, 아래 그림처럼 코드를 작성할 수 있는 페이지가 띄워집니다.

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_2.png)

녹색 박스로 표시된 영역에 아래 코드를 삽입한 뒤 'shift키 + enter키'를 눌러서 실행시킵니다.


```python
import scipy
import numpy
import matplotlib
import pandas
import sklearn
import pydotplus
import h5py

import theano
import tensorflow
import keras

print('scipy ' + scipy.__version__)
print('numpy ' + numpy.__version__)
print('matplotlib ' + matplotlib.__version__)
print('pandas ' + pandas.__version__)
print('sklearn ' + sklearn.__version__)
print('pydotplus ' + pydotplus.__version__)
print('h5py ' + h5py.__version__)

print('theano ' + theano.__version__)
print('tensorflow ' + tensorflow.__version__)
print('keras ' + keras.__version__)
```

각 패키지별로 버전이 표시되면 정상적으로 설치가 된 것입니다. 

#### 딥러닝 기본 모델 구동 확인

아래 코드는 기본적인 딥러닝 모델에 손글씨 데이터셋을 학습시킨 뒤 평가하는 기본 예제입니다. 새로운 셀에서 실행시키기 위해 상단 메뉴에서 'Insert > Insert Cell Below'을 선택하여 새로운 셀을 생성합니다. 새로 생긴 셀에 아래 코드를 입력한 후 'shift키 + enter키'를 눌러 해당 코드를 실행합니다.


```python
from keras.utils import np_utils
from keras.datasets import mnist
from keras.models import Sequential
from keras.layers import Dense, Activation

(X_train, Y_train), (X_test, Y_test) = mnist.load_data()
X_train = X_train.reshape(60000, 784).astype('float32') / 255.0
X_test = X_test.reshape(10000, 784).astype('float32') / 255.0
Y_train = np_utils.to_categorical(Y_train)
Y_test = np_utils.to_categorical(Y_test)

model = Sequential()
model.add(Dense(units=64, input_dim=28*28, activation='relu'))
model.add(Dense(units=10, activation='softmax'))
model.compile(loss='categorical_crossentropy', optimizer='sgd', metrics=['accuracy'])
model.fit(X_train, Y_train, epochs=5, batch_size=32)

loss_and_metrics = model.evaluate(X_test, Y_test, batch_size=32)

print('loss_and_metrics : ' + str(loss_and_metrics))
```

에러없이 다음과 같이 화면이 출력되면 정상적으로 작동되는 것입니다.

```
Epoch 1/5
60000/60000 [==============================] - 1s - loss: 0.6558 - acc: 0.8333     
Epoch 2/5
60000/60000 [==============================] - 1s - loss: 0.3485 - acc: 0.9012     
Epoch 3/5
60000/60000 [==============================] - 1s - loss: 0.3037 - acc: 0.9143     
Epoch 4/5
60000/60000 [==============================] - 1s - loss: 0.2759 - acc: 0.9222     
Epoch 5/5
60000/60000 [==============================] - 1s - loss: 0.2544 - acc: 0.9281     
 8064/10000 [=======================>......] - ETA: 0sloss_and_metrics : [0.23770418465733528, 0.93089999999999995]
 ```

#### 딥러닝 모델 가시화 기능 확인

아래 딥러닝 모델 구성을 가시화하는 코드입니다. 마찬가지로 새로운 셀에서 실행시키기 위해 상단 메뉴에서 'Insert > Insert Cell Below'을 선택하여 새로운 셀을 생성합니다. 새로 생긴 셀에 아래 코드를 입력한 후 'shift키 + enter키'를 눌러 해당 코드를 실행합니다.


```python
from IPython.display import SVG
from keras.utils.vis_utils import model_to_dot

%matplotlib inline

SVG(model_to_dot(model, show_shapes=True).create(prog='dot', format='svg'))
```

에러없이 다음과 같이 화면이 출력되면 정상적으로 작동되는 것입니다.

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_10.png)

설치가 정상적으로 완료되지 않고 ‘GraphViz's executables not found’ 또는 ‘Failed to import pydot. You must install pydot and graphviz for `pydotprint` to work.’ 문장이 뜨면서 에러가 나는 경우, 다음과 같이 진행합니다.

* http://www.graphviz.org/Download_windows.php 에 접속하여 graphviz-2.38.zip 파일을 다운로드 받습니다.
* 파일의 압축을 해제하고 graphviz를 설치합니다.
* 설치가 완료되면 제어판 > 시스템 및 보안 > 시스템 > 고급 시스템 설정 > 환경 변수에 다음과 같이 변수를 추가합니다.

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_11.png)

* 환경 변수의 [시스템 변수] 중 Path 에 다음과 같이 경로를 추가합니다.

```
    C:\Program Files (x86)\Graphviz2.38\bin
```

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_20.png)

* 환경 변수를 저장한 후 jupyter notebook이 실행되고 있는 cmd 창을 종료하고 다시 시작합니다.
* 다시 위 예제 코드를 실행시켜서 잘 그림과 같이 이미지가 잘 나오면 성공적으로 설치된 것입니다.

#### 딥러닝 모델 저장 기능 확인

아래 딥러닝 모델의 구성 및 가중치를 저장 및 로딩하는 코드입니다. 마찬가지로 새로운 셀에서 실행시키기 위해 상단 메뉴에서 'Insert > Insert Cell Below'을 선택하여 새로운 셀을 생성합니다. 새로 생긴 셀에 아래 코드를 입력한 후 'shift키 + enter키'를 눌러 해당 코드를 실행합니다.


```python
from keras.models import load_model

model.save('mnist_mlp_model.h5')
model = load_model('mnist_mlp_model.h5')
```

위 코드 실행 시 에러가 발생하지 않고, 로컬 디렉토리에 'mnist_mlp_model.h5' 파일이 생성되었으면 정상적으로 작동되는 것입니다. 지금까지 정상적으로 실행이 되었다면 상단 메뉴에서 'File > Save and Checkpoint'로 현재까지 테스트한 파일을 저장합니다. 

![img](http://tykimos.github.com/Keras/warehouse/2017-8-7-Keras_Install_on_Windows_4.png)

---

### 요약

윈도우 환경에서 케라스를 구동하기 위해, 주피터 노트북 개발환경, 주요 패치키, 딥러링 라이브러리 설치 및 구동을 해봤습니다. 

---

### 같이 보기

* [강좌 목차](https://tykimos.github.io/Keras/lecture/)
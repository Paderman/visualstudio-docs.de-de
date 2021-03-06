---
title: "Installieren von KI-Tools für Visual Studio"
description: "Installieren von KI-Tools für Visual Studio"
keywords: KI, Visual Studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: article
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 7e182a000dc9c8aaeb721b81036f878430260618
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="installation"></a>Installation

Visual Studio-Tools für Künstliche Intelligenz (KI) können auf 64-Bit-Windows-Betriebssystemen installiert werden.

## <a name="installing-visual-studio-tools-for-ai"></a>Installieren von Visual Studio-Tools für KI

Diese Erweiterung gilt für [Visual Studio](https://docs.microsoft.com/visualstudio/) 2015 und 2017 in der Community Edition oder höher.

Laden Sie die Tools zur Installation aus dem [Visual Studio MarketPlace](http://aka.ms/vstoolsforai) oder direkt in Visual Studio herunter.

1. **Tools**> **Erweiterungen und Updates**

![Installieren Sie CUDA unter Windows.](media\installation\extensions.png)

1. **Suchen Sie** in der oberen rechten Ecke nach „Tools für KI“.
2. Klicken Sie auf **Visual Studio-Tools für KI**.
3. Klicken Sie auf **Download**.


## <a name="preparing-your-local-machine"></a>Vorbereiten Ihres lokalen Computers

Bevor Sie Deep Learning-Modelle auf Ihrem lokalen Computer einrichten, sollten Sie sicherstellen, dass die neusten zutreffenden Anforderungen installiert sind. Prüfen Sie dabei auch, ob die neusten Treiber und Bibliotheken für Ihre NVIDIA-GPU (falls vorhanden) installiert sind. Außerdem sollten Sie sicherstellen, dass Python und Python-Bibliotheken wie NumPy und SciPy sowie passende Deep Learning-Frameworks, die Sie für das Projekt verwenden möchten, wie Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch und bzw. oder Chainer installiert sind.

> [!NOTE]
>
> Die Einführung in die Software in den folgenden Abschnitten sind Auszüge aus den jeweiligen Websites.

### <a name="nvidia-gpu-driver"></a>NVIDIA-GPU-Treiber

Deep Learning-Frameworks nutzen die NVIDIA-GPU, um Computer schnell und genau lernen zu lassen und auf Künstliche Intelligenz hinzuarbeiten. Wenn Ihr Computer über NVIDIA-GPU-Karten verfügt, klicken Sie auf diesen [Link](http://www.nvidia.com/Download/index.aspx), oder versuchen Sie, Ihr Betriebssystem zu aktualisieren und den neusten Treiber zu installieren.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) ist eine von NVIDIA erfundene Plattform für paralleles Computing und ein Programmiermodell.
Mithilfe dieses Tools können Sie die Computing-Leistung deutlich erhöhen, indem Sie die Leistung der GPU nutzen.
Derzeit ist das CUDA-Toolkit 8.0 für Deep Learning-Frameworks erforderlich.

So installieren Sie CUDA

- Gehen Sie auf diese [Website](https://developer.nvidia.com/cuda-80-ga2-download-archive), laden Sie CUDA herunter, und führen Sie die Installation durch.
- Achten Sie darauf, auch die CUDA-Laufzeitbibliotheken zu installieren, und fügen Sie anschließend den Umgebungsvariablen „%PATH%“ oder „$Path“ den Pfad der CUDA-Binärdatei hinzu.
- Unter Windows lautet der Pfad standardmäßig wie folgt: „C:\Programme\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin“.

![Installieren Sie CUDA unter Windows.](media\installation\install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Neural Network library) ist eine GPU-beschleunigte Bibliothek, die aus Primitiven für Deep Neural-Netzwerke von NVIDIA besteht. Deep Learning-Frameworks erfordern cuDNN Version 6.

So installieren Sie cuDNN
- Klicken Sie auf diesen [Link](https://developer.nvidia.com/rdp/cudnn-download), um das neuste Paket herunterzuladen und zu installieren.
- Achten Sie darauf, die Umgebungsvariablen „%PATH%“ oder „$Path“ dem Verzeichnis hinzuzufügen, das die cuDNN-Binärdatei enthält.
- Unter Windows können Sie „cudnn64_6.dll“ standardmäßig nach „C:\Programme\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin“ kopieren.

> [!NOTE]
>
> Für vorherige Deep Learning-Frameworks wie CNTK2.0 und TensorFlow 1.2.1 ist cuDNN v5.1 erforderlich.
> Allerdings können Sie auch mehrere cuDNN-Versionen gleichzeitig installieren.


### <a name="python"></a>Python

Python ist bis heute die führende Programmiersprache für Deep Learning-Anwendungen.
Eine **64-Bit**-Python-Verteilung ist erforderlich, und [Python 3.5.4](https://www.python.org/downloads/release/python-354/) wird empfohlen, um die bestmögliche Kompatibilität zu erreichen.

### <a name="to-install-python-on-windows"></a>So installieren Sie Python unter Windows
- Es wird empfohlen, dass Sie das Python-Startprogramm nur für sich selbst installieren und Python der Umgebungsvariablen „%PATH%“ hinzuzufügen.
- Stellen Sie sicher, dass pip installiert ist. Dabei handelt es sich um das Paketverwaltungssystem, das in Python geschriebene Softwarepakete installiert und verwaltet.

Deep Learning-Frameworks benötigen pip für die Installation.

![Installieren Sie Python unter Windows](media\installation\install_python_win.png)

Anschließend sollten Sie prüfen, ob Python 3.5 richtig installiert ist, und aktualisieren Sie pip auf die neuste Version, indem Sie den folgenden Befehl über ein Terminal ausführen:

- **Windows**
    ```cmd
    C:\Users\test>python -V
    Python 3.5.4

    C:\Users\test>pip3.5 -V
    pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

    C:\Users\test>python -m pip install -U pip
    ```

- **macOS**
    ```bash
    MyMac:~ test$ python3.5 -V
    Python 3.5.4

    MyMac:~ test$ pip3.5 -V
    pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

    MyMac:~ test$ python3.5 -m pip install -U pip
    ```

### <a name="python-on-visual-studio"></a>Python in Visual Studio

Python wird in Visual Studio vollständig über Erweiterungen unterstützt.
Erfahren Sie mehr über die Installation von [Python für Visual Studio-Tools](../python/installing-python-support-in-visual-studio.md).

### <a name="numpy-and-scipy"></a>NumPy und SciPy

- **NumPy** ein allgemeines Paket für die Verarbeitung von Arrays, dass dafür entwickelt wurde, große mehrdimensionale Arrays von beliebigen Aufzeichnungen zu bearbeiten, ohne dabei im Hinblick auf kleinere mehrdimensionale Arrays Geschwindigkeit einbüßen zu müssen.

- **SciPy** („Sei Pie“ ausgesprochen) ist eine von NumPy abhängige Open Source-Software für die Bereiche Mathematik, Wissenschaft und Ingenieurwesen.
SciPy enthält jetzt schon ab Version 1.0.0 offiziell vorkompilierte Wheel-Pakete für Windows.

Führen Sie den folgenden Befehl über ein Terminal aus, um NumPy und SciPy zu installieren:
```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
>
> Mithilfe des obenstehenden Befehls werden veraltete oder inoffizielle Versionen von NumPy und SciPy (z.B. Pakete von Drittanbietern für Windows von der Website http://www.lfd.uci.edu/~gohlke/pythonlibs/) auf die neusten offiziellen Versionen aktualisiert.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

Das [Microsoft Cognitive Toolkit](https://cntk.ai) ist ein einheitliches Deep Learning-Toolkit, das neuronale Netzwerke als eine Reihe von Rechenschritten in einem gerichteten Diagramm beschreibt. CNTK unterstützt die beiden Programmiersprachen Python und BrainScript.

> [!NOTE]
>
> Derzeit wird macOS von CNTK nicht unterstützt.

Informationen zur Installation des Python-Pakets für CNTK finden Sie unter [Installation von CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) ist eine Open Source-Softwarebibliothek für die numerische Berechnung mithilfe von Datenflussdiagrammen.
Ausführliche Informationen zur Installation finden Sie [hier](https://www.tensorflow.org/install/).

> [!NOTE]
>
> Ab Version 1.2 stellt TensorFlow keine GPU-Unterstützung für macOS mehr zur Verfügung.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) ist ein einfaches, modulares und skalierbares Deep Learning-Framework.
Caffe2, das auf dem Framework Caffe basiert, ist im Hinblick auf Ausdruck, Geschwindigkeit und Modularität konzipiert.

Derzeit ist kein vorkompiliertes Python-Wheel-Paket für Caffe2 verfügbar.

Gehen Sie auf diesen [Link](https://caffe2.ai/docs/getting-started.html), um Quellcode zum Erstellen zu verwenden.

### <a name="mxnet"></a>MXNet

[Apache MXNet (Incubating)](https://mxnet.incubator.apache.org/) ist ein Deep Learning-Framework, das im Hinblick auf Effizienz und Flexibilität konzipiert wurde.
Mithilfe dieses Frameworks können Sie die [symbolische mit der imperativen Programmierung](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) **vermischen**, um die Effizienz und Produktivität zu maximieren.

Führen Sie den folgenden Befehl über ein Terminal aus, um MXNet zu installieren:
- Mit GPU
    ```bash
    pip3.5 install mxnet-cu80==0.12.0
    ```
- Ohne GPU
    ```bash
    pip3.5 install mxnet==0.12.0
    ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) ist eine allgemeine neurale Netzwerk-API, die in Python geschrieben ist und zusätzlich zu CNTK, TensorFlow oder Theano ausgeführt werden kann. Das Tool wurde entwickelt, um schnelles Experimentieren zu ermöglichen. Ein Hauptbestandteil der Forschung ist, schnellstmöglich und ohne unnötige Verzögerungen von einer Idee zu einem Ergebnis zu gelangen.

Bitte führen Sie den folgenden Befehl über ein Terminal aus, um Keras zu installieren:
```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) ist eine Python-Bibliothek, über die Sie mathematische Ausdrücke mit mehrdimensionalen Arrays effizient definieren, optimieren und auswerten können.

Bitte führen Sie den folgenden Befehl über ein Terminal aus, um Theano zu installieren:
```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](http://pytorch.org/) ist ein Python-Paket mit zwei allgemeine Funktionen:
- Tensor-Berechnung (wie bei NumPy) mit hoher GPU-Beschleunigung
- Deep Neural-Netzwerke erstellen Builds auf einem bandbasierten Autograd-System

Bitte führen Sie den folgenden Befehl über ein Terminal aus, um PyTorch zu installieren:

- **Windows**
    - Derzeit gibt es noch kein offizielles Wheel-Paket. Sie können aber ein [Anaconda PyTorch-Paket](https://anaconda.org/peterjc123/pytorch/0.2.1/download/win-64/pytorch-0.2.1-py35h24644ff_0.2.1cu80.tar.bz2) eines Drittanbieters herunterladen.
    - Dekomprimieren Sie es in Ihr Basisverzeichnis, z.B.: „C:\Users\test\pytorch“.
    - Fügen Sie „C:\Users\test\pytorch\Lib\site-packages“ der Umgebungsvariablen „%PYTHONPATH%“ hinzu.

- **macOS**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
    ```
    > [!NOTE]
    >
    > macOS-Binärdateien unterstützen CUDA nicht. Führen Sie daher eine Installation aus der Quelle durch, wenn CUDA benötigt wird.

- **Linux**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
    ```
    > [!NOTE]
    >
    > Dieses einzelne Paket unterstützt sowohl GPU als auch CPU.

Installieren Sie zuletzt Torchvision unter allen anderen Betriebssystemen außer Windows:
```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) ist ein Python-basiertes Deep Learning-Framework, das für Flexibilität steht.
Das Framework stellt automatische Differenzierungs-APIs, die auf **Define-by-run-Ansätzen** (auch unter der Bezeichnung „Dynamic Computational Graphs“ („Dynamische Berechnungsdiagramme“) bekannt) basieren, sowie objektorientierte, allgemeine APIs zur Verfügung, über die neurale Netzwerke erstellt und trainiert werden.

Installieren Sie [CuPy](https://github.com/cupy/cupy), um die CUDA-Unterstützung zu aktivieren:
```bash
pip3.5 install cupy
```

> [!NOTE]
>
> Unter Windows benötigen Sie [Microsoft Visual Studio](https://www.visualstudio.com/) Version **2015** oder [Microsoft Visual C++ Build Tools](http://landinghub.visualstudio.com/visual-cpp-build-tools), um CuPy mit CUDA 8.0 zu kompilieren.

Bitte führen Sie den folgenden Befehl über ein Terminal aus, um Chainer zu installieren:
```bash
pip3.5 install chainer==3.0.0
```



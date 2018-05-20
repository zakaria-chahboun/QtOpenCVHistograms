# QtOpencvHistograms

Hi :) ***`QtCvHistogram`*** is a simple *class* for calculate normal **`histograms`** and **`cumulative histograms`**

for both **`RGB or BGR`** images and for **`grayscale`** images,

using *Qt* for displaying the result in **`QPixmap`**.

### Explanations :

the ***`QtCvHistogram`*** class, has two **static** methods

First method has **two arguments** :
- input image: ***`cv:Mat`***
- the histogram cumulative or not: ***`bool`***
- this function return **`QVector<cv::Mat>`**, this vector has ***3 elements*** for colored images or ***one element*** for gray image:

```cpp
QVector<cv::Mat> hist =  QtCvHistogram::calculation(cv::Mat input, bool isCumulative = false);
```

Second method has **three arguments** :
- **input histogram vector:**
- **size of output image**
- **color of background output image**

```cpp
QVector<QPixmap> draw(QVector<cv::Mat> hist, QSize imSize = QSize(512,400), QColor backColor = QColor(255,255,255));
```

---------------------
### Error(s)

If you get ***`hist.size() == 0`*** this is an error!

-----------------------

### Example :
```cpp
    // Load Image
    cv::Mat im = cv::imread("image.jpg");

    // List or Vector for calculing Histograms
    QVector<cv::Mat> hist =  QtCvHistogram::calculation(im);
    
    // List or Vector for drawing Histograms
    QVector<QPixmap> draw = QtCvHistogram::draw(hist,QSize(256,200));

    // if a grayscale image
    if(hist.size() == 1)
    ui->image->setPixmap(draw[0]);

    // or if a colored image
    if(hist.size() == 3){
        ui->blue->setPixmap(draw[0]);
        ui->green->setPixmap(draw[1]);
        ui->red->setPixmap(draw[2]);
    }
```

### Screenshots :

*Normal Histograms*
<img src="https://raw.githubusercontent.com/zakaria-chahboun/QtOpencvHistograms/master/screenshot1.png" />

*Cumulative Histograms*
<img src="https://raw.githubusercontent.com/zakaria-chahboun/QtOpencvHistograms/master/screenshot2.png" />

------------------------------

19/05/2018

twitter : <a href="https://twitter.com/zaki_chahboun">here</a>

facebook : <a href="https://www.facebook.com/zakaria.chahboun.2018">here</a>

Gmail : Zakaria.Chahboun.1996@Gmail.com

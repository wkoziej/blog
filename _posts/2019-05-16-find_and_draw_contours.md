---
layout: post
title: "find_and_draw_contours"
tags:
    - python
    - notebook
--- 
# Załóż kontur na maskę lub odwrotnie 
 
O tym jak można sobie z notebooka działać na blogu... 

**In [1]:**

{% highlight python %}
import sys
import os
module_path = os.path.abspath(os.path.join('..'))
if module_path not in sys.path:
    sys.path.append(module_path)
    
### !!!! DLACZEGO    
module_path = '/home/wojtas/dev/work/mate/python'    
if module_path not in sys.path:
    sys.path.append(module_path)
module_path ='/home/wojtas/dev/work/venv/lib/python3.7/site-packages'
if module_path not in sys.path:
    sys.path.append(module_path)
    
import logging
# import assecobs.mate
# print(assecobs.mate.__version__)
import cv2
import tensorflow as tf
import matplotlib.pyplot as plt

# from assecobs.mate.bbox.bounding_box_builder import BoundingBoxBuilder
# from assecobs.mate.bbox.bounding_box_renderer import BoundingBoxRenderer
# from assecobs.mate.bbox.bounding_box_visuals import BoundingBoxVisuals, LabelPosition
import pandas as pd
import json
from pandas.io.json import json_normalize
{% endhighlight %}

**In [2]:**

{% highlight python %}
tf.test.is_gpu_available()
{% endhighlight %}




    True



**In [3]:**

{% highlight python %}
ls '/home/wojtas/dev/work/test'
{% endhighlight %}

    [0m[01;35mImage0001.png[0m  [01;35mtest2.png[0m  [01;35mtest.png[0m


**In [4]:**

{% highlight python %}
import numpy as np
import cv2 as cv
plt.rcParams['figure.figsize'] = [40, 40]
im = cv.imread('test/test2.png')
imgray = cv.cvtColor(im, cv.COLOR_BGR2GRAY)
ret, thresh = cv.threshold(imgray, 225, 255, 0)
contours, hierarchy = cv.findContours(thresh, cv.RETR_TREE, cv.CHAIN_APPROX_SIMPLE)
{% endhighlight %}

**In [5]:**

{% highlight python %}
cnt = [contours[0]]
im2 = cv.drawContours(im, cnt, -1, (0,255,0), 3)
plt.imshow(im)
{% endhighlight %}




    <matplotlib.image.AxesImage at 0x7ff21e085f28>



 
![png]({{ BASE_PATH }}/assets/images/2019-05-16-find_and_draw_contours_6_1.png) 


**In [7]:**

{% highlight python %}
!pwd
{% endhighlight %}

    /home/wojtas/dev/work

 
## Konwertujemy do md i wrzucamy na blog 

**In [29]:**

{% highlight python %}
output="2019-05-16-find_and_draw_contours"
{% endhighlight %}

**In [28]:**

{% highlight python %}
!jupyter nbconvert find_and_draw_contours.ipynb --to markdown --config jekyll.py --output={output}
!cp ./{output}_files/*.png /home/wojtas/dev/blog/assets/images
!cp ./{output}.md /home/wojtas/dev/blog/_posts

{% endhighlight %}

    [NbConvertApp] Converting notebook find_and_draw_contours.ipynb to markdown
    [NbConvertApp] Support files will be in 2019-05-16-find_and_draw_contours_files/
    [NbConvertApp] Making directory /home/wojtas/dev/work/2019-05-16-find_and_draw_contours_files
    [NbConvertApp] Writing 3539 bytes to /home/wojtas/dev/work/2019-05-16-find_and_draw_contours.md


**In [22]:**

{% highlight python %}
!pwd
{% endhighlight %}

    /home/wojtas/dev/work


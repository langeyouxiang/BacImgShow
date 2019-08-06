# BacImgShow<br>  
双边滤波的解释<br>  
https://www.cnblogs.com/Imageshop/p/3406823.html<br>  


```Python
#读取 佳能 raw图片，有色差，待解决。
import numpy as np 
import cv2 
import imageio as ii
import rawpy as rp

raw = rp.imread('625A8999.CR2')
#output_bps=16表示输出是 16 bit 
im = raw.postprocess(use_camera_wb=True, half_size=False, no_auto_bright=True, output_bps=16)
#取得图片原始高度与宽度
height, width = im.shape[:2]
#缩放 
size = (int(width*0.2), int(height*0.2))
shrink = cv2.resize(im, size, interpolation = cv2.INTER_AREA)
cv2.imshow("raw",shrink) 
cv2.waitKey()
cv2.destroyAllWindows()
```

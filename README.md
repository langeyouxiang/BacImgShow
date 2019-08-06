# BacImgShow<br/>  
双边滤波的解释<br/>  
https://www.cnblogs.com/Imageshop/p/3406823.html<br/>

#Python3.7 安装opencv并设置国内代理。如安装其他第三方python库，请修改opencv-python为自己所需的第三方库名字。<br/>
pip install opencv-python -i https://mirrors.ustc.edu.cn/pypi/web/simple/


```Python
#np.float32(im / 65535.0*255.0) 出现memory error时检查下系统是否是64位，安装的python是32位。将python重新安装位64位。
#读取佳能raw图片，有色差，待解决。
import numpy as np 
import cv2 
import imageio as ii
import rawpy as rp

raw = rp.imread('625A8999.CR2')
#output_bps=16表示输出是 16 bit 
im = raw.postprocess(use_camera_wb=True, half_size=False, no_auto_bright=True, output_bps=16)
#rgb = np.float32(im / 65535.0*255.0)
#rgb = np.asarray(rgb,np.uint8)
#取得图片原始高度与宽度
height, width = im.shape[:2]
#缩放 
size = (int(width*0.2), int(height*0.2))
shrink = cv2.resize(im, size, interpolation = cv2.INTER_AREA)
cv2.imshow("raw",shrink) 
cv2.waitKey()
cv2.destroyAllWindows()
```

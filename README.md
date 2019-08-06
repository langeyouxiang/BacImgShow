# BacImgShow<br>  
双边滤波的解释<br>  
https://www.cnblogs.com/Imageshop/p/3406823.html<br>  


读取 佳能 raw图片，有色差，待解决。<br>  
import numpy as np<br>  
import cv2<br>  
import imageio as ii<br>  
import rawpy as rp<br>  

raw = rp.imread('625A8999.CR2')<br>  
output_bps=16表示输出是 16 bit <br>  
im = raw.postprocess(use_camera_wb=True, half_size=False, no_auto_bright=True, output_bps=16)<br>  
取得图片原始高度与宽度<br>  
height, width = im.shape[:2]<br>  
缩放<br>  
size = (int(width*0.2), int(height*0.2))<br>  
shrink = cv2.resize(im, size, interpolation = cv2.INTER_AREA)<br>  
cv2.imshow("raw",shrink)<br>  
cv2.waitKey()<br>  
cv2.destroyAllWindows()<br>  

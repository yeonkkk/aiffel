# ๐ํ๋ก์ ํธ
[CutMix, Mixup ๋น๊ต ํ๋ก์ ํธ](https://github.com/yeonkkk/AIFFEL-Project/blob/main/GoingDeeper02/%5BGD2%5Daugmentation.ipynb)  

<br>

๐ํ๋ก์ ํธ ํ์ผ์ด ์ด๋ฆฌ์ง ์๋๋ค๋ฉด ํ๊ธฐ ๋งํฌ๋ฅผ ์ด์ฉํด์ฃผ์ธ์!  
[Jupyter Notebook Viewer](https://nbviewer.org/github/yeonkkk/AIFFEL-Project/blob/main/GoingDeeper02/%5BGD2%5Daugmentation.ipynb)

<br><br>

# GD2. ์ ๋ง๋  Augmentation, ์ด๋ฏธ์ง 100์ฅ ์๋ถ๋ฝ๋ค.
> **Data Augmentation**: ์ฃผ์ด์ง ๋ฐ์ดํฐ์์ ๋ค์ํ ๋ฐฉ๋ฒ์ผ๋ก ์ฆ๊ฐ์์ผ(augment) ํ์ต ๋ฐ์ดํฐ์์ ๊ท๋ชจ๋ฅผ ๋๋ฆฌ๋ ๋ฐฉ๋ฒ

<br>

- `augmentation`์ ์ฅ์ 
  - ๋ฐ์ดํฐ๊ฐ ๋ง์์ง๋ฉด ๊ณผ์ ํฉ์ ์ค์ผ ์ ์๋ค.
  - augmentation์ ํตํด์ ์ค์  ์๋ ฅ๊ฐ๊ณผ ๋น์ทํ ๋ฐ์ดํฐ ๋ถํฌ๋ฅผ ๋ง๋ค์ด ๋ผ ์ ์๋ค.
  - ๋ธ์ด์ฆ์ ์ ๋์ํ  ์ ์๋ค.

<br><br>

## Image Augmentation ๊ธฐ๋ฒ
ํ์ํ๋ก์ฐ ํ์ด์ง๋ฅผ ์ฐธ๊ณ  ํ์์ต๋๋ค.  


<br><br>


### Flipping
> ์ข์ฐ ๋๋ ์ํ๋ก ์ด๋ฏธ์ง๋ฅผ ๋์นญํ๋ ๊ธฐ๋ฅ

- ์ ํํ ๋ต์ด ์กด์ฌํ๋ ๋ฌธ์ (detection, segmentation ๋ฑ)์ ์ ์ฉํ  ๊ฒฝ์ฐ ๋ผ๋ฒจ๋ flipping ํด์ค์ผ ํ๋ค.

<br><br>
<br><br>

### Gray scale
>  3๊ฐ์ง ์ฑ๋์ ๊ฐ์ง RGB ์ด๋ฏธ์ง๋ฅผ ํ๋์ ์ฑ๋์ ๊ฐ์ง๊ฒ ํ๋ ๊ธฐ๋ฅ

<br><br>
<br><br>

### Saturation
> RGB ์ด๋ฏธ์ง๋ฅผ HSV ์ด๋ฏธ์ง๋ก ๋ณ๊ฒฝํ๊ณ  S(saturation) ์ฑ๋์ ์คํ์(offset)์ ์ ์ฉ

- `HSV`: Hue(์์กฐ), Saturation(์ฑ๋), Value(๋ช๋) 3๊ฐ์ง ์ฑ๋ถ์ผ๋ก ํํ  

- ์ด๋ฏธ์ง๋ฅผ ๋ณด๋ค ์ ๋ชํ๊ฒ ๋ง๋ ๋ค.

- ์ ์ฉ ํ ๋ค์ RGB ์์ ๋ชจ๋ธ๋ก ๋ณ๊ฒฝ

<br><br>
<br><br>

### Brightness
> ๋ฐ๊ธฐ ์กฐ์   
> RGB ์ฑ๋์์ ๊ฐ์ ๋ํด์ฃผ๋ฉด ๋ฐ์์ง๊ณ , ๋นผ์ฃผ๋ฉด ์ด๋์์ง๋ ์ฑ์ง์ ์ด์ฉํ์ฌ Brightness๋ฅผ ๋ณ๊ฒฝ  

<br><br>
<br><br>

### Rotation
> ์ด๋ฏธ์ง์ ๊ฐ๋ ๋ณํ

- 90๋ ๋จ์ ๋ณํ โ ์ง์ฌ๊ฐํ ํํ๊ฐ ์ ์ง, ์ด๋ฏธ์ง ํฌ๊ธฐ ์กฐ์  ์ ๋ฐ๋ก ์ฌ์ฉ ๊ฐ๋ฅ

- ์ด ์ธ์ ๊ฒฝ์ฐ ๋น ์์ญ์ด ์๊ธฐ๊ฒ ๋๋ค.

<br><br>
<br><br>

### Center Crop
> ์ด๋ฏธ์ง ์ค์์ ๊ธฐ์ค์ผ๋ก ํ๋ํ๋ ๋ฐฉ๋ฒ

- ๋๋ฌด ์๊ฒ ์ ์ฉํ  ๊ฒฝ์ฐ ๋ผ๋ฒจ๊ณผ ๋ง์ง ์๋ ์ํฉ์ด ๋ฐ์ํ  ์ ์์


<br><br>
<br><br>

### ์ด์ธ augmentation
- Gaussian noise
- Contrast change
- Sharpen
- Affine transformation
- Padding
- Blurring


<br><br>
<br><br>

## ์ฐธ๊ณ  ์๋ฃ

[Tensorflow: Data augmentation](https://www.tensorflow.org/tutorials/images/data_augmentation)

[์์์ธ์๊ณผ ์์๋ชจ๋ธ(Gray,RGB,HSV,YCbCr)](https://darkpgmr.tistory.com/66)





# πνλ‘μ νΈ
νλ‘μ νΈ νμΌμ΄ μ΄λ¦¬μ§ μλλ€λ©΄ νκΈ° λ§ν¬ μ€ νλλ₯Ό μ΄μ©ν΄μ£ΌμΈμ!  
[μ½λ© λ§ν¬](https://colab.research.google.com/drive/1OnPXSFDgCtyQ3tQXFxkyHJ08s2KcrbBn?usp=sharing)  
[Jupyter Notebook Viewer](https://nbviewer.org/github/yeonkkk/AIFFEL-Project/blob/main/Exploration16/project/%5BE_16%5DSRGAN.ipynb)  

<br><br>

# E-16. νλ¦° μ¬μ§μ μ λͺνκ²

`Super Resolution`μ μ¬μ©νμ¬ μ ν΄μλμ μ΄λ―Έμ§λ₯Ό κ³ ν΄μλμ μ΄λ―Έμ§λ‘ λ³ννλ€.  

`GAN`μ μ λ°ν κ³ ν΄μλ μ΄λ―Έμ§λ₯Ό μμ±νκΈ°μ ν¨κ³Όμ μ΄μ§λ§ μκ°μ΄ μ€λκ±Έλ¦°λ€λ νΉμ§μ΄ μλ€.  

<br><br>

## Super Resolution
> Super Resolution(μ΄ν΄μν): μ ν΄μλ μμμ κ³ ν΄μλ μμμΌλ‘ λ³ννλ μμ  

<br>

`ν½μ`: λμ€νλ μ΄λ₯Ό κ΅¬μ±νλ κ°μ₯ μμ λ¨μ  

`RGB`: λΉμ 3μμμ νΌν©νμ¬ μμ λνλ΄λ λ°©μ  

`ν΄μλ`: ν½μμ κ°μκ° λ§μμλ‘ μ λͺν΄μ§λ€(κ³ ν΄μλ).

`CCTV`  ν΄μλ λ¬Έμ , `μλ£ μμ` λ±μ ν¨κ³Όμ μΌλ‘ μ¬μ©λ  μ μλ€.  

<br><br>

### Super Resolution νμ© μ λ¬Έμ μ 

- **ill-posed (inverse) problem**: 1κ°μ μ ν΄μλ μ΄λ―Έμ§μ λν΄ λ€μμ κ³ ν΄μλ μ΄λ―Έμ§κ° λμ¬ μ μλ μ 

- **super Resolution λ¬Έμ μ λ³΅μ‘λ**: μ νλ μ λ³΄λ§μ μ΄μ©ν΄ λ§μ μ λ³΄λ₯Ό λ§λ€μ΄λ΄λ κ³Όμ μ λ§€μ° λ³΅μ‘ν¨ β μλͺ»λ μ λ³΄ μμ± κ°λ₯μ± μ¦κ°

- **μ λμ  νκ° μ²λ**μ **μ¬λμ μκ°μ  κ΄μ°° νκ°**κ° μ μΌμΉνμ§ μμ  

<br><br>

## Interpolation
> λ³΄κ°λ²(interpolation): κ°μ μκ³  μλ λ μ  μ¬μ΄ μ§μ μ κ°μ΄ μΌλ§μΌμ§λ₯Ό μΆμ νλ κΈ°λ².  
>  λ§μ λ₯λ¬λ κΈ°λ° Super Resolution μ°κ΅¬μμ κ²°κ³Όλ₯Ό λΉκ΅νκΈ° μν΄ μν  

<br>

`μ νλ³΄κ°λ²(linear interpolation)`: λ μ  μ¬μ΄μ μ§μ μ μ΄μ©ν΄ f(x)λ₯Ό μΆμ   
![image](https://user-images.githubusercontent.com/88660886/142337121-392ea204-aaab-42b6-8302-795f07505209.png)  
    [μ΄λ―Έμ§ μΆμ²](https://bskyvision.com/789)

<br><br>

`μΌμ°¨λ³΄κ°λ²(cubic interpolation)`: 3μ°¨(cubic) ν¨μλ₯Ό νμ©νμ¬ f(x)λ₯Ό μΆμ . μ νλ³΄κ°λ²κ³Ό λ¬λ¦¬ λ€ κ°μ μ μ μ°Έμ‘°  
![image](https://user-images.githubusercontent.com/88660886/142337324-f25394a0-4e98-4491-b786-59d2c80ec379.png)  
    [μ΄λ―Έμ§ μΆμ²](https://bskyvision.com/789)


`μμ νλ³΄κ°λ²(bilinear interpolation)`: μ νλ³΄κ°λ²μ 2μ°¨μμΌλ‘ νμ₯μν¨ κ². 4(=2x2)κ°μ μ  μ°Έμ‘°   

`μμΌμ°¨λ³΄κ°λ²(bicubic interpolation)`: μΌμ°¨λ³΄κ°λ²μ 2μ°¨μμΌλ‘ νμ₯μν¨ κ². 16(=4x4)κ°μ μ μ μ°Έμ‘°   

<br><br>

## SRCNN
> Super Resolution Convolutional Neural Networks.  
> MSE(Mean Squared Error) loss function μ¬μ©  

![image](https://user-images.githubusercontent.com/88660886/142338447-2bf6a5c8-602f-4ff5-9c78-6b79a8292e94.png)  
[μ΄λ―Έμ§ μΆμ²](https://deepai.org/publication/deep-learning-for-single-image-super-resolution-a-brief-review)  

<br>

- κ³Όμ 
  
  - Patch extraction and representation: μ ν΄μλ μ΄λ―Έμ§μμ patch μΆμΆ
  - Non-linear mapping: λ€μ°¨μμ patchλ€μ non-linearνκ² λ€λ₯Έ λ€μ°¨μμ patchλ€λ‘ λ§€ν
  - Reconstruction: λ€μ°¨μ patchλ€λ‘λΆν° κ³ ν΄μλ μ΄λ―Έμ§λ₯Ό λ³΅μ

<br><br>

## μ΄μΈ κ΅¬μ‘°λ€

### VDSR (Very Deep Super Resolution)
- μ ν΄μλ μ΄λ―Έμ§μ ν¬κΈ°λ₯Ό λλ € μλ ₯μΌλ‘ μ¬μ© (interpolation)
- 20κ°μ convolutional layer
- residual learning μ΄μ©: κ³ ν΄μλ μ΄λ―Έμ§ μμ± μ§μ  μλ³Έ μ΄λ―Έμ§λ₯Ό λν¨

<br><br>

### RDN (Residual Dense Network)
-  κ° layerμμ λμ€λ μΆλ ₯μ μ΅λν νμ© β μΆλ ₯λ νΉμ§λ€μ μ΄νμλ μ¬νμ©

<br><br>

### RCAN (Residual Channel Attention Networks)
- κ°κ°μ νΉμ§ λ§΅μ λμμΌλ‘ μΌλΆ μ€μν μ±λμλ§ μ νμ μΌλ‘ μ§μ€νλλ‘ μ λ(Channel attention)

<br><br>

## SRGAN
> Super Resoultion + GAN: GAN(Generative Adversarial Networks) μ νμ©ν Super Resolution 

![image](https://user-images.githubusercontent.com/88660886/142344382-34b54035-28a7-4b5f-9d80-2526e464024d.png)  
[μ΄λ―Έμ§ μΆμ²](https://arxiv.org/pdf/1609.04802.pdf)

- k: kernel size, n: νν°μ μ, s: stride 

- μμ±λ μ΄λ―Έμ§μ μ€μ  μ΄λ―Έμ§λ₯Ό μ΄λ―Έμ§λ·μΌλ‘ μ¬μ  νμ΅λ VGG λͺ¨λΈμ μλ ₯νμ¬ λμ€λ feature mapμμμ μ°¨μ΄λ₯Ό κ³μ°

- `perceptual loss` = `content loss` + `adversarial loss`
    
    - `content loss`: VGGλ₯Ό μ΄μ©ν loss
    - `adversarial loss`: GANμ μ¬μ©ν¨μΌλ‘μ¨ λ°μνλ loss

<br><br>

### GAN(Generative adversarial network)
> μ λ°μ΄ν°κ° κ°μ§κ³  μλ νλ₯ λΆν¬λ₯Ό μΆμ νλλ‘ νκ³ , μΈκ³΅μ κ²½λ§μ΄ κ·Έ λΆν¬λ₯Ό λ§λ€μ΄ λΌ μ μλλ‘ νλ€

- λλ€λ³μμ λν νλ₯ λΆν¬λ₯Ό μλ€ β λλ€λ³μ μ¦ λ°μ΄ν°μ λν μ λΆλ₯Ό μ΄ν΄νκ³  μλ€!

- Generator: νμ΅ μλ£ ν λ°μ΄ν°μ νλ₯ λΆν¬λ₯Ό λ°λ₯΄λ μλ‘μ΄ λ°μ΄ν° μμ±

- Discriminator: νμ΅ μλ£ ν λΆλ₯μ μλ―Έκ° μλ 0.5μ νλ₯ κ°μ μΆλ ₯

<br><br>

## PSNR
> peak Signal-to-Noise Ratio.  
> μμ λ΄μμ κ°μ§ μ μλ μ΅λ μ νΈ λ μ‘μ(noise) λΉ  

- μμμ μμΆνμ λ νμ§μ΄ μΌλ§λ μμ€λμλμ§ νκ°νλ λͺ©μ μΌλ‘ μ¬μ©  

- λ°μλ²¨(db) λ¨μ  

- λμμλ‘ μλ³Έμ λΉν΄ μμ€μ΄ μ λ€λ μλ―Έ  

<br><br>
## SSIM
> Structural Similarity Index Map  
> μΌλ§λ κ΅¬μ‘° μ λ³΄λ₯Ό λ³νμν€μ§ μμλμ§λ₯Ό κ³μ°  

- λμμλ‘ μλ³Έ νμ§μ κ°κΉλ€λ μλ―Έ


<br><br>

## μ°Έκ³  μλ£

[λͺ¨λν°μ ν΅μ¬, λμ€νλ μ΄μ μ€ν λ°λΌμ‘κΈ°](https://news.lgdisplay.com/kr/2014/03/%eb%aa%a8%eb%8b%88%ed%84%b0-%ed%95%b5%ec%8b%ac-%eb%94%94%ec%8a%a4%ed%94%8c%eb%a0%88%ec%9d%b4%ec%9d%98-%ec%8a%a4%ed%8e%99-%eb%94%b0%eb%9d%bc%ec%9e%a1%ea%b8%b0-%ed%95%b4%ec%83%81%eb%8f%84/)

[κ·Έλ¦ΌμΌλ‘ μ½κ² μμλ³΄λ HD ν΄μλμ μ°¨μ΄](https://news.lgdisplay.com/kr/2014/07/%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%89%BD%EA%B2%8C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-hd-%ED%95%B4%EC%83%81%EB%8F%84%EC%9D%98-%EC%B0%A8%EC%9D%B4/)

[νμκ±°ν λ¦¬λ§μ€ν°λ§ μ μκΈ°](http://tech.kobeta.com/%ED%95%98%EC%96%80%EA%B1%B0%ED%83%91-uhd-%EB%A6%AC%EB%A7%88%EC%8A%A4%ED%84%B0%EB%A7%81-%EC%A0%9C%EC%9E%91%EA%B8%B0/)

[Deep Learning for Single Image Super-Resolution:
A Brief Review](https://arxiv.org/pdf/1808.03344.pdf)

[μ νλ³΄κ°λ²κ³Ό μΌμ°¨λ³΄κ°λ², μ λλ‘ μ΄ν΄νμ](https://bskyvision.com/789)

[ilinear interpolation μμ ](https://blog.naver.com/dic1224/220882679460)

[OpenCV Documentation](https://docs.opencv.org/4.x/da/d54/group__imgproc__transform.html#ga5bb5a1fea74ea38e1a5445ca803ff121)

[λΌλ¬Έλ¦¬λ·° - SRCNN](https://d-tail.tistory.com/6)

[GAN - μ€μ€λ‘ νμ΅νλ μΈκ³΅μ§λ₯](https://www.samsungsds.com/kr/insights/Generative-adversarial-network-AI.html)

[GAN - GANμ κ°λκ³Ό μ΄ν΄](https://www.samsungsds.com/kr/insights/Generative-adversarial-network-AI-2.html)

[μ΅λμ νΈλμ‘μλΉ(PSNR)μ μ΄λ―Έμ§ νμ§](https://bskyvision.com/392)

[2D μ΄λ―Έμ§ νμ§ νκ°μ κ΅¬μ‘°λ³νλ₯Ό λ°μνλ SSIMκ³Ό κ·Έμ λ³νλ€](https://bskyvision.com/396)

[κ³΅μ ν AI μΌκ΅΄μΈμκΈ°](https://www.kakaobrain.com/blog/57)

[Single Image Super Resolution using Deep Learning Overview](https://hoya012.github.io/blog/SIngle-Image-Super-Resolution-Overview/)

[PR12 - SRCNN](https://www.youtube.com/watch?v=1jGr_OFyfa0)

[PR12 - SRGAN](https://www.youtube.com/watch?v=nGPMKnoJTcI)

[EDSR](https://www.youtube.com/watch?v=OMIqkn2DCUk)

[λ₯λ¬λ Super Resolution μ΄λκΉμ§ μλ?](https://www.youtube.com/watch?v=nvsYKSHw0jo)


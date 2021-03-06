## ๐ํ๋ก์ ํธ
ํ๋ก์ ํธ ํ์ผ์ด ์ด๋ฆฌ์ง ์๋๋ค๋ฉด ํ๊ธฐ ๋งํฌ๋ฅผ ์ด์ฉํด์ฃผ์ธ์!  
[Jupyter Notebook Viewer](https://nbviewer.org/github/yeonkkk/AIFFEL-Project/blob/main/Exploration19/%5BE-19%5Dpix2pix.ipynb)  

<br><br>

# E-19. ๋ ์ค์ผ์น๋ฅผ ํ  ํ๋ ๋๋ ์ฑ์์ ํ๊ฑฐ๋ผ
> ์กฐ๊ฑด ์๋ ์์ฑ๋ชจ๋ธ(unconditioned generative model)์ ์์ฑํ๊ณ ์ ํ๋ ๋ฐ์ดํฐ์ ๋ํ ์ ์ด๊ฐ ์ด๋ ค์  

<br><br>


## GAN
>  Generator์ Discriminator ์ ๊ฒฝ๋ง์ด minimax game์ ํตํด ์๋ก ๊ฒฝ์ํ๋ฉฐ ๋ฐ์ ํ๋ ๊ตฌ์กฐ.  
์กฐ๊ฑด ์๋ ์์ฑ๋ชจ๋ธ(unconditioned generative model)  

<br><br>

![](https://images.velog.io/images/tjddus0302/post/28a4bbac-a06c-4b9d-bae1-fead7667d710/image.png)

```
์ถ์ฒ: AIFFEL EXPLORATION_SSAC2 19. ๋ ์ค์ผ์น๋ฅผ ํ  ํ๋ ๋๋ ์ฑ์์ ํ๊ฑฐ๋ผ  
```

<br><br>

#### Generator
- ๋ธ์ด์ฆ z ์๋ ฅ โ ํน์  representation(๊ฒ์ ์) ๋ณํ โ ๊ฐ์ง ๋ฐ์ดํฐ G(z) ์์ฑ   

#### Discriminator
- ์ค์  ๋ฐ์ดํฐ x์ ๊ฐ์ง ๋ฐ์ดํฐ G(z)๋ฅผ ์๋ ฅ โ D(x), D(G(z)) (๋ณด๋ผ์) ๊ณ์ฐ (์ง์ง, ๊ฐ์ง ์๋ณ)    


<br><br>
<br><br>

### GAN์ ๋ชฉ์  ํจ์
![CodeCogsEqn (1)](https://user-images.githubusercontent.com/88660886/145061774-a07470e5-f6ea-4841-9c41-ac1811b16322.png)


<!-- $$
{min_G}{max_D} {V(D,G)}=\mathbb{E}_{x\sim p_{data}~(x)}[log D(x)] + \mathbb{E}_{z\sim p_x(z)}[log(1-D(G(z)))]
$$    -->

<br><br>
<br><br>


## cGAN(Conditional Generative Adversarial Nets)
> GAN์ด ๊ฐ์ง ์์ฑ ๊ณผ์ ์ ๋ถํธํจ์ ํด์.  
> ์ํ๋ ์ข๋ฅ์ ์ด๋ฏธ์ง๋ฅผ ์์ฑํ๋๋ก ๊ณ ์๋ ๋ฐฉ๋ฒ  

<br><br>

![](https://images.velog.io/images/tjddus0302/post/0f5dd9ef-4c57-43f5-ae03-5a22f9a2f865/image.png)

```
์ถ์ฒ: AIFFEL EXPLORATION_SSAC2 19. ๋ ์ค์ผ์น๋ฅผ ํ  ํ๋ ๋๋ ์ฑ์์ ํ๊ฑฐ๋ผ  
```

<br><br>

#### Generator  
- z์ ์ถ๊ฐ ์ ๋ณด y ์๋ ฅ๋ฐ์ โ Generator ๋ด๋ถ์์ ๊ฒฐํฉ โ representation(๊ฒ์ ์)์ผ๋ก ๋ณํ โ ๊ฐ์ง ๋ฐ์ดํฐ G(zโฃy) ์์ฑ  

- MNIST๋ CIFAR-10 ๋ฑ์ ๋ฐ์ดํฐ์์ ๋ํด ํ์ต์ํค๋ ๊ฒฝ์ฐ y๋ ๋ ์ด๋ธ ์ ๋ณด, ์ผ๋ฐ์ ์ผ๋ก one-hot ๋ฒกํฐ๋ฅผ ์๋ ฅ์ผ๋ก ๋ฃ์  


#### Discriminator
- x์ G(zโฃy) ๊ฐ๊ฐ ์๋ ฅ๋ฐ์ โ y ์ ๋ณด๊ฐ ํจ๊ป ์๋ ฅ โ ์ง์ง์ ๊ฐ์ง๋ฅผ ์๋ณ  

- MNIST๋ CIFAR-10 ๋ฑ์ ๋ฐ์ดํฐ์์ ๋ํด ํ์ต์ํค๋ ๊ฒฝ์ฐ x์ y๋ ์๋ง์ ํ ์("7"์ด๋ผ ์ฐ์ธ ์ด๋ฏธ์ง์ ๊ฒฝ์ฐ ๋ ์ด๋ธ๋ 7)์ ์ด๋ค์ผ ํจ.  


<br><br>
<br><br>

### cGAN์ ๋ชฉ์  ํจ์
![CodeCogsEqn (3)](https://user-images.githubusercontent.com/88660886/145063109-b31a1ebd-4bf6-44d2-b927-8a5d1f9a51ff.png)
<!-- $$
{min_G}{max_D} {V(D,G)}=\mathbb{E}_{x\sim p_{data}~(x)}[log D(x)] + \mathbb{E}_{z\sim p_x(xโฃy)}[log(1-D(G(xโฃy)))]
$$
 -->
- G์ D์ ์๋ ฅ์ ํน์  ์กฐ๊ฑด์ ๋ํ๋ด๋ ์ ๋ณด์ธ y๋ฅผ ๊ฐ์ด ์๋ ฅ  

- y๋ ์์ ๋ธ์ด์ฆ ์๋ ฅ์ธ z์ ๊ฐ์ด๋์ ๊ฐ์  

<br><br>
<br><br>

## Pix2Pix
> ์ด๋ฏธ์ง๋ฅผ ์๋ ฅ์ผ๋ก ํ์ฌ ์ํ๋ ๋ค๋ฅธ ํํ์ ์ด๋ฏธ์ง๋ก ๋ณํ์ํฌ ์ ์๋ GAN ๋ชจ๋ธ  

- Conditional Adversarial Networks๋ก Image-to-Image Translation์ ์ํ    

-  GAN ๊ธฐ๋ฐ์ Image-to-Image Translation ์์์์ ๊ฐ์ฅ ๊ธฐ์ด๊ฐ ๋๋ ์ฐ๊ตฌ  

<br><br>
<br><br>

### Pix2Pix Generator

![](https://images.velog.io/images/tjddus0302/post/afbbc616-bf0e-4fe5-96d0-0e38420b2c41/image.png)

<br><br>

-  ์๋ ฅ ์ด๋ฏธ์ง์ ๋ณํ๋ ์ด๋ฏธ์ง์ ํฌ๊ธฐ๋ ๋์ผํด์ผ ํจ  

- Encoder: ์๋ ฅ ์ด๋ฏธ์ง(x) ๋ฐ์ โ ๋จ๊ณ์ ์ผ๋ก ์ด๋ฏธ์ง down-sampling โ representation ํ์ต  
 
- Decoder: ์ด๋ฏธ์ง up-sampling โ ์๋ ฅ ์ด๋ฏธ์ง์ ๋์ผํ ํฌ๊ธฐ์ ์ด๋ฏธ์ง(y) ์์ฑ  

- ์ ๊ณผ์ ์ ๋ชจ๋ convolution ๋ ์ด์ด๋ก ์งํ  

- `bottleneck`  

	- Encoder์ ์ต์ข ์ถ๋ ฅ  
	
    	- ์ ์ด๋ฏธ์ง ์ค๊ฐ์ ๊ฐ์ฅ ์์ ์ฌ๊ฐํ  
    
   	 - ์๋ ฅ ์ด๋ฏธ์ง(x)์ ๊ฐ์ฅ ์ค์ํ ํน์ง๋ค์ ๋ด๊ณ  ์์  

<br><br>
<br><br>

###  U-Net
![](https://images.velog.io/images/tjddus0302/post/3e6f6f42-00ea-40e3-a913-c7c863c62570/image.png)

<br><br>

- ๋ ์ด์ด๋ง๋ค Encoder, Decoder ์ฐ๊ฒฐ(skip connection)๋์ด ์์  

- Encoder๋ก๋ถํฐ ๋ ๋ง์ ์ถ๊ฐ ์ ๋ณด๋ฅผ ์ป๋ ๋ฐฉ๋ฒ


<br><br>
<br><br>

### Pix2Pix Loss Function

- `L1(MAE)` or `L2(MSE)` ์์ค๋ง ์ด์ฉํ์ฌ ํ์ต โ ๊ฒฐ๊ณผ ํ๋ฆฟํ ๊ฒฝํฅ

- `L1+cGAN`:  L1์์ค๊ณผ GAN ์์ค์ ๊ฐ์ด ์ฌ์ฉํ์ฌ ๋ ์ข์ ๊ฒฐ๊ณผ ๋์ถ


<br><br>
<br><br>

### Pix2Pix Discriminator
![](https://images.velog.io/images/tjddus0302/post/3c6fca05-0c63-4430-ad57-3b2c89cc1ebe/image.png)
```
์ถ์ฒ : https://arxiv.org/pdf/1803.07422.pdf
```

#### PatchGAN
> ๊ฑฐ๋ฆฌ๊ฐ ๋จผ ๋ ํฝ์์ ์๋ก ์ฐ๊ด์ฑ์ด ๊ฑฐ์ ์๊ธฐ ๋๋ฌธ์ ํน์  ํฌ๊ธฐ๋ฅผ ๊ฐ์ง ์ผ๋ถ ์์ญ์ ๋ํด์ ์ธ๋ถ์ ์ผ๋ก ์ง์ง/๊ฐ์ง๋ฅผ ํ๋ณ

- Discriminator์ ์ด๋ฏธ์ง ์๋ ฅ

- convolution ๋ ์ด์ด๋ฅผ ๊ฑฐ์ณ ํ๋ฅ ๊ฐ์ ๋ํ๋ด๋ ์ต์ข ๊ฒฐ๊ณผ ์์ฑ(์ฌ๋ฌ ๊ฐ์ ๊ฐ)

- ์ ์ฒด ์์ญ์ด ์๋ ์ผ๋ถ ์์ญ์ ๋ํด์๋ง ์ง์ง/๊ฐ์ง๋ฅผ ํ๋ณํ๋ ํ๋์ ํ๋ฅ ๊ฐ ๋์ถ

- ๊ฐ์ ํ๊ท ํ์ฌ ์ต์ข Discriminator์ ์ถ๋ ฅ์ ์์ฑ

- ๋๋ฌด ์์ patch๋ ํ์ง์ด ๋จ์ด์ง ์ ์์

<br><br>
<br><br>

## ์ฐธ๊ณ  ์๋ฃ
[TF2-GAN](https://github.com/thisisiron/TF2-GAN)  

[[๋ผ์จํผํ] Stochastic Pooling & Maxout
](https://m.blog.naver.com/PostView.nhn?blogId=laonple&logNo=221259325819&proxyReferer=&proxyReferer=https:%2F%2Fwww.google.com%2F)  


[[Paper] Maxout Networks](https://arxiv.org/pdf/1302.4389.pdf)  

[Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/pdf/1611.07004.pdf)  


[U-Net ๋ผ๋ฌธ ๋ฆฌ๋ทฐ](https://medium.com/@msmapark2/u-net-%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0-u-net-convolutional-networks-for-biomedical-image-segmentation-456d6901b28a)  



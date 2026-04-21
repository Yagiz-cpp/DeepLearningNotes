## Logistic Regression

Altdaki denklem bizim w agirligindaki ve b bias'indaki lagistic regressionumuz 
$$
\hat{y} = \sigma (w^T x + b)
$$
Sigmoid'e alma sebebimiz burda biz bir kedi tahmin denklemi yaziyoruz ve cevabin 1 ve 0 olmasini istiyoruz ama siqmoidsiz yazarsak denklem gordugun gibi negatif veya 1'in ustunde bir deger alabilir sinirlamak icin sigmoid denklemi icine aldik.
$$
\sigma(z) = \frac{1}{1+e^z}
$$


### Logistic Regression Cost Function
Burdaki amacimiz w ve b degerlerini (agirlik ve bias degerlerini) olcmek nerelerde tahmin dogru nerelerde yanlis ona bakicaz

#### Loss(Error) Function  
$$ L(\hat{y},y) = \frac{1}{2}(\hat{y}-y)^2 $$
![[Pasted image 20260418195912.png|186]]
bu hata olcme denklemi kullanilmiyor. Cunku yerel minimum degerleri var ve burda en dusuk degeri yani en dusuk hata oranini bulmak zorlasiyor

**Kullanilan Denklem**
$$
L(\hat{y},y) = -(y\log{\hat{y}} + (1-y)\log{1-\hat{y}})
$$
burda bildigin gibi kedi bulma denklemi dusunuyoruz ve resim ya kedidir yada degildir.
$$
\hat{y} = Bizim-kedi-tahminimiz
$$
$$
y = kedi-olup-olmama-durumu
$$
 Burda 2 durumuz var. Eger kedi ise y = 1 dir ve sadece:
$$
y\log{\hat{y}}
$$
kullanicaz. Digerinin katsayisi 0 oluyor cunku.

Ama burda bu sadece bir durumda olan hata. 

Tum hatalarin ortalamasini almak icin kullandigimiz denklem:
$$
J(w,b) = \frac{1}{m} \sum^{m}_{i=1}L(\hat{y}^{(i)}, y^{(i)}
) = - \frac{1}{m}\sum^m_{i=1}y^{(i)}\log({\hat{y}^{(i)}}) + (1 - y^{(i)})log({1-\hat{y}^{(i)}}) $$
Bizim ana amacimiz burda J(w,b) nin en dusuk olmasi icin gereken w ve b degerlerini bulmak boylelikle daha tutarli bir modelimiz olur.

Peki nasil bu degerleri bulabiliriz ?

#### Gradient Descent

![[Pasted image 20260418210025.png|298]]

Burda gosterimi kolay olsun diye sadece w yi aldik eger b yide alirsak 3 boyutlu bir grafik olurdu(cizemezdik iste:D). 

Ama mantik ayni genel olarak bir adim sayisi belirliyoruz ve onu o andaki konumumuzun turevi(egimi) ile carpip w geri toplayip yeni w elde ediyoruz (Bi sik anlamadin ama denkleme bak anlarsin)
$$
w = w - \alpha\frac{dJ(w)}{dw}
$$
Burdaki a(alpha ama ben a dicem) adim katsayisinni temsil ediyor
![[Pasted image 20260418210700.png|291]] Mantigini soldaki resimden de anlayabilirsin.

Kisa Not = Adam Turev videosu koymus:D. ADAM TUREVI 4 VIDEODA ANLATMIS AQ.

#### Vectorization

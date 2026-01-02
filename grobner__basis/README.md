
# 動作を確認した環境:


```bash
# `build_info();`の実行結果
(%i1) build_info();
(%o1)
Maxima-version: "5.47.0"
Maxima build date: "2023-06-02 20:31:42"
Host type: "x86_64-w64-mingw32"
Lisp implementation type: "SBCL"
Lisp implementation version: "2.3.2"
User dir: "C:/Users/XYZ/maxima"
Temp dir: "C:/Users/XYZ/AppData/Local/Temp"
Object dir: "C:/Users/XYZ/maxima/binary/5_47_0/sbcl/2_3_2"
Frontend: false
```


実施したこと: [1] "Maximaで学ぶコンピュータ代数 赤間世紀 工学社 2010年" にグレブナー基底の計算手順が記載されていた。
それを参考に、
[2] "グレブナー基底とその応用 丸山正樹 共立出版株式会社 2002年" のp82に記載されている以下のイデアルのグレブナー基底をMaximaで計算してみた。
(このグレブナー基底を計算しようと思った動機:  [2]のp82に以下の記載があったから。)
>このイデアルのグレブナー基底を辞書式順序で計算すると驚くほど複雑であることがわかる。
>とても手計算でできるものではなく、能力の低い計算機代数のソフトでは相当待っても答えが出ない。ソフトと計算機の能力判定に使える例ともいえる。
> 計算機代数のソフトが手近にあったら一度試してみられたい。





```math
K[x,y,z] \ni f_1 (x,y,z)=x^5+y^4+z^3-1, f_2 (x,y,z)=x^3+y^3+z^2-1

\\
\mathfrak{J}=(f_1, f_2)

\\
この時、イデアル \mathfrak{J}=(f_1, f_2)の グレブナー基底を x>y>z の斉次逆辞書式順序で求めよ。



```


ところがmaximaで実際に
```lisp
load(affine)$

grobner_basis([x^5+y^4+z^3-1,x^3+y^3+z^2-1]);

```
でグレブナー基底を求めたら、違う値がでた (原因は単項式順序の指定が)


## Maximaで学ぶコンピュータ代数 赤間世紀 工学社 2010年
## グレブナー基底とその応用 丸山正樹 共立出版株式会社 2002年
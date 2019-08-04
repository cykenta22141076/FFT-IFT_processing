# FFT-IFT_processing

まずimreadで画像を読み込む
img_gray=cv2.cvtColor(image,cv2.COLOR_RGB2GRAY)でグレースケール化
次にfimg = np.fft.fft2(img_gray)でグレースケール化したものをフーリエ変換すると周波数領域の原点(直流成分)が画像の左上の角に位置するようになる．
直流成分を画像中心に移動させたければ，スペクトル全体を \frac{N}{2} 両方向のずらす必要がある．
この移動には np.fft.fftshift() 関数を用いる.
magnitude_spectrum = 20*np.log(np.abs(fshift))で複素数の絶対値を取っている.

class　mouseParamはhttps://teratail.com/questions/167652より引用

H,W = img_gray.shape以降の処理はhttps://gist.github.com/ginrou/5e443b42aabe73664b41をもとに作成
screen(クリックした座標の波形を保存するよう)とcanvas(クリックした座標の波形を足しわせるよう)を準備する
forの二重ループはクリックから得られる最大回数までに設定
getPosより座標を入手しそれぞれの処理に利用
最後にそれぞれをプロットする


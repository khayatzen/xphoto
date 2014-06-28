xphoto
======

XPhoto - Extention for Yii Framework to upload photo and capture from webcam or camera using HTML5

* Licenced under WTFPL - http://wtfpl.net
* Author: Muhammad Khayat
* Blog: http://yat.my.id
* Twitter: @khayate
* Thanks to @pujexx and @avriqq who inspired me to make this extension 


Requirements:
============
- Twitter Bootstrap
- Yii 1.1 above


How to use it:
================
Call on your view:
------------------
~~~
[php]
$this->widget('ext.xphoto.XPhoto',array(
 	'model'=>$model,
 	'attribute'=>'user_photo',
));
~~~

Call on your controller action:
-------------------------------
~~~
[php]
if (!empty($_POST['Profile']['user_photo']))
{
    $foto = $_POST['Profile']['foto'];
    //Decode with base64
    $foto = str_replace('data:image/png;base64,', '', $foto);
    $foto = str_replace(' ', '+', $foto);
    $data_foto = base64_decode($foto);
    
    //Set photo filename
    $filename = Yii::app()->user->name.'.png';
    $filepath = YiiBase::getPathOfAlias("webroot").'/uploads/userphotos/'.$filename;

    $writeToDisk = file_put_contents($filepath, $data_foto);                        
}
~~~


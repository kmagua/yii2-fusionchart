Fusonchart for Yii2
=======================
widget render Chart with fusonchart

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist ptrnov/yii2-fusionchart "*"
```

or add

```
"ptrnov/yii2-fusionchart": "*"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, simply use it in your code by  :

```php
	/**
	 * RUNNING IN FUSIONCHART TYPE
	 * column2d,column3d,bar2d
	 * Type,  Ref: http://www.fusioncharts.com/dev/demos/chart-gallery.html
	 * color, Ref: http://dmcritchie.mvps.org/excel/colors.htm
	*/

	//Controllers
	use ptrnov\fusionchart\Chart;
	//use ptrnovlab\models\Userlogin;
	
	public function actionIndex()
    {
		$model =Userlogin::find()->all(); 				// your Model, example from class user
		$testChart= Chart::Widget([
			'dataArray'=>$model,						//array scource model or manual array or sqlquery
			'dataField'=>['username','id'],				//field['label','value'], normaly value is numeric
			'type'=>'column3d',							//Chart Type 
			'renderid'=>'chartContainer',				//unix name render
			'chartOption'=>[				
					'caption'=>'judul Header',			//Header Title
					'subCaption'=>'judul Sub',			//Sub Title
					'xaxisName'=>'Month',				//Title Bawah/ posisi x
					'yaxisName'=>'Jumlah', 				//Title Samping/ posisi y									
					'theme'=>'fint',					//Theme
					'palettecolors'=> "#583e78,#008ee4,#f8bd19,#e44a00,#6baa01,#ff2e2e",
					'bgColor'=> "#ffffff",				//color Background / warna latar 
					'showBorder'=> "0",					//border box outside atau garis kotak luar
					'showCanvasBorder'=> "0",			//border box inside atau garis kotak dalam	
			],
		]);
			
		return $this->render('index',[
				'testChart'=>$testChart
			]);
	}
	
	//views index
	use ptrnov\fusionchart\ChartAsset;
	ChartAsset::register($this);
	
	<div><?=$testChart?></div>
```


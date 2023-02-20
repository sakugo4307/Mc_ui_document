# document
## _ui_defs.json
```json
{
  "ui_def":["list string"]
}
```

jsonを認識するためのファイルです  
すべてuiのjsonのファイルを指定します  
**自分で新しくjsonを作った場合ここに書かないと認識しません**  
string例:`"ui/example_ui.json"`



## 他のui一般


### **必須**"namespace":{string}

他のjsonファイルで、このファイルに存在する要素を引用するときに使用します  
例`"namespace":{"example_ui"}`


### "name":{object} / "name@(引用元namespace.)引用元name":{object}

nameは自らで決めることができます　nameに`@`や`.`を使うのは避けましょう  

まず、短い書き方と長い書き方があります  
uiのjson内では他のjsonファイル内の要素を引用することができるのですが、その場合引用元を記す必要があります  
引用をした場合引用元のプロパティをそのまま適応され、上書きが可能です  
()内は同じjson内で引用をする時は短縮可能です  

引用しない場合は前者の書き方で問題ありません

object内には様々なプロパティを書き、ここがuiの最も大切な部分です

例:`"example_panel":{}`
 `"example_panel_2@example_ui.example_panel":{}`


## "name":{object}内  
ここがuiを構成する上で非常に重要なものとなります

### "type":{string}
typeによって使用できるプロパティが異なります  
用途にあったtypeを選択してください  
string内  
`image,stack_panel,label,input_panel,panel,grid,factory,custom,button,selection_wheel,screen,scroll_view,toggle,carousel_label,slider_box,slider,dropdown,edit_box,scroll_track,scrollbar_box`    
例:`"type":"image"`


### imageプロパティ一覧
**"type":"image"**  
主に画像を表示する時に使います
使用できるプロパティは以下の通り


property|description|option|option_description|example
---|---|---|---|---
"texture":{string}|表示する画像のファイルを指定します| | |"texture":"texture/ui/example_image"  
"clip_direction":{string}|解析中|left<br>right|解析中|"clip_direction":"left"  
"clip_pixelperfect":{bool}|解析中|true<br>false|解析中|
"anchor_from":{string}<br>"anchor_to":{string}|imageをどこに寄せるかを指定します<br>ここで決めた位置が始点になります<br>2つの違いについては解析中|top_right<br>top_left<br>top_middle<br>middle_right<br>middle_left<br>bottom_right<br>bottom_left<br>bottom_middle<br>center|右上<br>左上<br>中央上<br>右中央<br>左中央<br>右下<br>右上<br>中央下<br>画面中央|"anchor_from":"top_left"<br>"anchor_to":"top_left"
"size":[list string]|textureで指定した画像をsizeの大きさに変更します<br>[縦の長さ,横の長さ]という風に記述します|number<br>px<br>%<br>%c<br>%cm<br>%x<br>%y<br>default<br>fill| |"size":[16,32]<br>"size":["100%c - 10px",default"]
"layer":{number}|複数の画像が重なった際に値の大きい方が上に表示されます<br>同じ値の画像が重なった場合非常に見にくくなります|数字||"layer":1
"offset":[list_string]|始点の位置からの場所を指定します<br>anchor_from<br>anchor_toで決めた始点を0とし,上方向へマイナス 下方向へプラス 左方向へマイナス 右方向へプラスという風になっています|number<br>px<br>%
"uv_size":[list string]|忘れた
"uv":{string}|imageに反映するアニメーションを指定します|@+(引用元namespace.)アニメーションのname||"uv":@example_anim
"disable_anim_fast_forward":{bool}|調査中|ture<br>false
"texture_file_system":{string}|調査中<br>テクスチャのファイル関連<br>スクショ関連に使われる模様|
"color":[list string]|画像の色を変更します<br>元の色が白以外は黒くっぽくなります<br>rgbの割合で表記されます|0~1||"color":[0,0,0.6670]
"alpha":{number}|透明度を設定します|0<br>~<br>1|完全透明<br><br>不透明|"alpha":0.8
"force_texture_reload"|調査中
"fill":{bool}|sizeで指定した大きさが100%以下の時、その大きさに画像を切り抜きます?|true<br>false|切り抜く<br>伸縮(default)|"fill":true
"visible":{bool}|透明か否か<br>trueの時ボタン当の機能を中に付けた場合見えないが動作はする|true<br>false|透明<br>非透明|"visible":true
"tiled":{bool}|画像を格子状に並べるかどうかを決定します|true<br>false|並べる<br>並べない|"tiled": true
"tiled_scale":[list string]|tiledで並べる画像の1つ1つの大きさを設定します|||"tlied_scale":[0.5,0.5]
"max_size"<br>"min_size"|調査中<br>おそらくsizeをuilangで書いた時の最大値,最小値を設定する
"bilinear"|調査中
"anims"|調査中
"zip_folder"|調査中
"ignored":{bool}|すべてのプロパティが無効化するかどうかを決定します|true<br>false|無効<br>有効|"ignored":true
"priority"|調査中
"keep_ratio"|調査中
"use_anchored_offset"|調査中
"grayscale":{bool}|調査中|true<br>flase
"clip_ratio"|調査中
"allow_debug_missing_texture":{bool}|テクスチャが読み込めなかった際に代わりにエラー画像を出すかどうかを決定します|true<br>false|表示する<br>表示しない|"allow_debug_missing_texture": false
"follows_cursor"|調査中
"propagate_alpha"|調査中
"animation_reset_name"|調査中

**"bindings":[list object]**  
条件式によって画像の表示、非表示が切り替えられる模様  
また他の機能もある  
調査中  
"binding_name"  
"binding_name_override"  
"binding_type":
"binding_collection_name":

**"variables":[list object]**  
なんか条件式でどうのこうの  
調査中  
"requires"  

**"property_bag":{object}**
"#helper_link":


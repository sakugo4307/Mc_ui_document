# document
## _ui_defs.json

jsonを認識するためのファイルです  
すべてuiのjsonのファイルを指定します  
自分で新しくjsonを作った場合ここに書かないと認識しません  

### Parameters
parameter|type|description
---|---|---
ui_def|string|uiファイルのパス




## 他のui一般


### **必須**"namespace":{string}

他のjsonファイルで、このファイルに存在する要素を引用するときに使用します  
例`"namespace":{"example_ui"}`


### "name":{object} / "name@継承元namespace.継承元name":{object}

nameは自らで決めることができます　nameに`@`や`.`を使うのは避けましょう  

まず、短い書き方と長い書き方があります  
uiのjson内では他のjsonファイル内の要素を継承することができるのですが、その場合継承元を記す必要があります  
継承をした場合引用元のプロパティをそのまま適応され、上書きが可能です  
継承元namespaceは同じjson内で継承をする時は短縮可能です  

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


property|type|description|option|option_description|example
---|---|---|---|---|---
texture|string|画像ファイルのパス| | |"texture":"texture/ui/example_image"  
clip_direction|string|解析中|left<br>right|解析中|"clip_direction":"left"  
clip_pixelperfect|bool|解析中|true<br>false|解析中|
anchor_from<br>anchor_to|string|imageの始点　fromで大まかな位置を決める　toでformで決めた位置に当たる部分を決める|top_right<br>top_left<br>top_middle<br>middle_right<br>middle_left<br>bottom_right<br>bottom_left<br>bottom_middle<br>center|右上<br>左上<br>中央上<br>右中央<br>左中央<br>右下<br>右上<br>中央下<br>画面中央|"anchor_from":"top_left"<br>"anchor_to":"top_left"
size|string|画像をsizeの大きさに変更<br>[縦,横]|number<br>px<br>%<br>%c<br>%cm<br>%x<br>%y<br>default<br>fill| |"size":[16,32]<br>"size":["100%c - 10px",default"]
layer|number|複数の画像が重なった際に値の大きい方が上に表示|数字||"layer":1
offset|string|始点の位置からの座標<br>anchor_from<br>anchor_toで決めた始点を0とし,上- 下+ 左- 右+|number<br>px<br>%
uv_size|string|アニメーションをする際の１フレームの大きさ|number||"uv_size":[16,16]
uv|string|imageに反映するアニメーション|@継承namespace.アニメーションのname||"uv":@example_anim
disable_anim_fast_forward|bool|調査中|ture<br>false
texture_file_system|string|調査中<br>テクスチャのファイル関連<br>スクショ関連に使われる模様|
color|string|画像の色を変更<br>rgbの割合で表記|0~1||"color":[0,0,0.6670]
alpha|string|透明度<br>alphaアニメーションの指定|0<br>~<br>1<br>@namespace.name|完全透明<br><br>不透明<br>animation依存|"alpha":0.8
force_texture_reload|bool|調査中|true<br>false
fill|bool|sizeで指定した大きさが100%以下の時、その大きさに画像を切り抜く|true<br>false|切り抜く<br>縮小|"fill":true
visible|bool|透明か否か<br>trueの時ボタン当の機能を中に付けた場合見えないが動作はする|true<br>false|透明<br>非透明|"visible":true
tiled|bool|画像を格子状に並べる|true<br>false|並べる<br>並べない|"tiled": true
tiled_scale|string|tiledで並べる画像の1つ1つの大きさ|||"tlied_scale":[0.5,0.5]
max_size<br>min_size|string|調査中<br>おそらくsizeをuilangで書いた時の最大値,最小値を設定する
bilinear|bool|調査中|true<br>false
anims|object|調査中
zip_folder|string|調査中
ignored|bool|すべてのプロパティが無効化|true<br>false|無効<br>有効|"ignored":true
priority|number|調査中|true<br>false
keep_ratio|bool|調査中|true<br>false
use_anchored_offset|bool|調査中
grayscale|bool|調査中|true<br>flase
clip_ratio|nymber|調査中
allow_debug_missing_texture|bool|テクスチャが読み込めなかった際に代わりにエラー画像を使用する|true<br>false|使用する<br>使用しない|"allow_debug_missing_texture": false
follows_cursor|bool|調査中|true<br>false
propagate_alpha|bool|調査中|true<br>false
animation_reset_name|string|調査中

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

### labelプロパティ一覧  

## animation  
### "anim_type":{string}  
typeでanimationを指定することはできません  
animationを使う場合はtypeの代わりにanim_typeを使います  
anim_typeではanimationの種類をします  
string内  
`alpha,offset,size,flip_book,uv,color,wait,aseprite_filp_book,clip`  
### flip_bookプロパティ一覧
"anim_type":"filp_book"
横に並べた画像をフレームごとにコマ送りにします

property|type|description|option|option_description|example
---|---|---|---|---|---
initial_uv|string|
frame_count|string|フレーム数|number
frame_step|string|フレームの幅|number
fps|string|再生速度|number
easing|string||linear
next|string|次に再生するアニメーション|@namespace.name||
resettable|bool||true<br>flase
reversible|bool|幅まで表示したときに折り返す|true<br>false|折り返す<br>始めに戻る
duration|string|アニメーションをする時間|number

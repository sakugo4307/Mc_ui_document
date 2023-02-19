"_ui_defs.json"内専用？
{
  "ui_def":[list string]
}

jsonを認識するためのファイルです
uiのjsonのファイルを指定します
自分で新しくjsonを作った場合ここに書かないと認識しません

例:"ui/example_ui.json"



他のui一般


必須"namespace":{string}

他のjsonファイルで、このファイルに存在する要素を引用するときに使用します
例"namespace":{example_ui}


"名前空間":{object}
又は
"名前空間@(引用元namespace.)引用元名前空間":{object}

uiのjson内では他のjsonファイルを引用することができます
その場合下の書き方で引用元を書く必要があります
引用をした場合引用元のプロパティをそのまま適応され、上書きも可能です
()内は同じjson内で引用をする時は短縮可能です

引用をしない場合は上の書き方で問題ありません
object内には様々なプロパティを書き、ここがuiの最も大切な部分です

例:"example_panel":{}
 "example_panel_2@example_ui.example_panel":{}


"名前空間":{object}内

"type":{string}
typeによって使用できるプロパティが異なります
用途にあったtypeを選択してください
string内
image,stack_panel,label,input_panel,panel,grid,factory,custom,button,selection_wheel,screen,scroll_view,toggle,carousel_label,slider_box,slider,dropdown,edit_box,scroll_track,scrollbar_box


プロパティ一覧
    "type":"image"
    主に画像を表示する時に使います
    使用できるプロパティは以下の通り

    "texture":{string},
    表示する画像のファイルを指定します
    例"texture":"texture/ui/example_image"

    "clip_direction":{string},
    解析中
    string内
    left,
    例"clip_direction":"left"

    "clip_pixelperfect":{bool},
    解析中

    "anchor_from":{string},
    "anchor_to":{string},
    imageをどこに寄せるかを指定します
    ここで決めた位置が始点になります
    2つの違いについては解析中
    string内
    top_right,top_left,top_middle,middle_right,middle_left,bottom_right,bottom_left,bottom_middle,center
    高さ top:上 middle:真ん中 bottom:下
    左右 right:右 middle:真ん中left:左
    高さ＿左右
    画面の中央に寄せる際はcenterにしてください
    例"anchor_from":"top_left"
      "anchor_to":"top_left"

    "size":[list string],
    textureで指定した画像をsizeの大きさに変更します
    縦横比が元の画像と違う場合引き伸ばされます
    [縦の長さ,横の長さ]という風に記述します
    string内
    数字やui内だけの特殊な数式で書かれます
    uilang(適当)は複雑なため用検証

    "layer":{number},
    レイヤーです
    複数の画像が重なった際に値の大きい方が上に表示されます
    同じ値の画像が重なった場合非常に見にくくなります
    例:"layer":1


    "bindings":{object},
    条件式によって画像の表示、非表示が切り替えられる模様
    また他の機能もある
    調査中

    "offset":[list_string],
    始点の位置からの場所を指定します
    [縦,横]
    anchor_from
    anchor_to
    で決めた始点を0とし,上方向へマイナス 下方向へプラス 左方向へマイナス 右方向へプラスという風になっています
    

    'uv_size',
    忘れた
    
    'uv',
    忘れた
    
    'disable_anim_fast_forward',
    調査中
    
    'texture_file_system',
    調査中
    
    'color',
    色
    画像にどの様な挙動をするか未確認
    
    "alpha":{number},
    透明度
    
    'force_texture_reload',
    調査中
    
    'fill'
    調査中,
    
    "visible":{bool},
    透明か否か
    trueで透明 falseで非透明
    trueの時ボタン当の機能を中に付けた場合見えないが動作はする
    
    'tiled',
    調査中
    
    'max_size',    
    'min_size',
    調査中
    おそらくsizeをuilangで書いた時の最大値,最小値を設定する
    
    'bilinear',
    調査中
    
    'anims'
    調査中,

    'zip_folder',
    調査中

    "ignored":{bool},
    uiプロパティを有効か無効か
    trueで無効 falseで有効
    有効にした場合はすべてのプロパティが無効化される
    texture等も無効化され透明になる模様
    trueの時ボタン当の機能を中に付けた場合押せない

    'variables',
    なんか条件式でどうのこうの
    調査中

    'priority',
    調査中

    'property_bag',
    調査中

    'keep_ratio',
    調査中

    'use_anchored_offset',
    調査中

    'grayscale',
    調査中

    'clip_ratio',
    調査中

    'allow_debug_missing_texture',
    調査中

    'tiled_scale',
    調査中

    'follows_cursor',
    調査中

    'propagate_alpha',
    調査中

    'animation_reset_name'
    調査中



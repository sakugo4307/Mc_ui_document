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
anchor_from<br>anchor_to|string|imageの始点　fromで大まかな位置を決める　toでformで決めた位置に当たる部分を決める|top_right<br>top_left<br>top_middle<br>middle_right<br>middle_left<br>bottom_right<br>bottom_left<br>bottom_middle<br>center|右上<br>左上<br>中央上<br>右中央<br>左中央<br>右下<br>右上<br>中央下<br>画面中央|"anchor_from":"top_left"<br>"anchor_to":"top_left"
size|string|画像をsizeの大きさに変更<br>[縦,横]|number<br>px<br>%<br>%c<br>%cm<br>%x<br>%y<br>default<br>fill| |"size":[16,32]<br>"size":["100%c - 10px",default"]
layer|number|複数の画像が重なった際に値の大きい方が上に表示|数字||"layer":1
offset|string|始点の位置からの座標<br>anchor_from<br>anchor_toで決めた始点を0とし,上- 下+ 左- 右+|number<br>px<br>%
uv_size|string|アニメーションをする際の１フレームの大きさ|number||"uv_size":[16,16]
uv|string|imageに反映するアニメーション|@継承namespace.アニメーションのname||"uv":@example_anim
disable_anim_fast_forward|bool|不明|ture<br>false
texture_file_system|string|調査中<br>テクスチャのファイル関連<br>スクショ関連に使われる模様|
color|string|画像の色を変更<br>rgbの割合で表記|0~1||"color":[0,0,0.6670]
alpha|string|透明度<br>alphaアニメーションの指定|0<br>~<br>1<br>@namespace.name|完全透明<br><br>不透明<br>animation依存|"alpha":0.8
propagate_alpha|bool|子要素にも親のalphaを適応する|true<br>false|する<br>しない
fill|bool|sizeで指定した大きさが100%以下の時、その大きさに画像を切り抜く|true<br>false|切り抜く<br>縮小|"fill":true
visible|bool|透明か否か<br>trueの時ボタン当の機能を中に付けた場合見えないが動作はする|true<br>false|透明<br>非透明|"visible":true
tiled|bool|画像を格子状に並べる|true<br>false|並べる<br>並べない|"tiled": true
tiled_scale|string|tiledで並べる画像の1つ1つの大きさ|||"tlied_scale":[0.5,0.5]
max_size<br>min_size|string|sizeの最大値,最小値|number<br>px<br>%<br>%c||"max_size":["100%",20]
ignored|bool|すべてのプロパティが無効化|true<br>false|無効<br>有効|"ignored":true
allow_debug_missing_texture|bool|テクスチャが読み込めなかった際に代わりにエラー画像を使用する|true<br>false|使用する<br>使用しない|"allow_debug_missing_texture": false
priority|number|調査中|true<br>false
keep_ratio|bool|調査中|true<br>false
use_anchored_offset|bool|不明
grayscale|bool|不明|true<br>flase
clip_ratio|nymber|調査中
clip_direction|string|解析中|left<br>right|解析中|"clip_direction":"left"  
clip_pixelperfect|bool|解析中|true<br>false|解析中|
follows_cursor|bool|調査中|true<br>false
animation_reset_name|string|調査中
force_texture_reload|bool|不明|true<br>false
bilinear|bool|不明|true<br>false
zip_folder|string|不明
animes|string|

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
**"type":"label"**  
主に文字を表示する時に使います
使用できるプロパティは以下の通り


property|type|description|option|option_description|example
---|---|---|---|---|---
color|strin
anchor_from|string
anchor_to|string
layer|string
offset|string
size|string
text|string
shadow|bool
localize|
font_type|string
font_scale_factor
max_size
font_size
property_bag
text_alignment
text_tts
line_padding
tts_override_control_value
visible
locked_alpha
anims
tts_skip_message
ignored
alpha
min_size
enable_profanity_filter
locked_color
inherit_max_sibling_height
priority
notify_on_ellipses
hide_hyphen
inherit_max_sibling_width
tts_name
tts_control_type_order_priority
tts_value_order_priority
backup_font_type
tts_section_header


bindings
variables

### panelプロパティ一覧  
**"type":"panel"**  
主にパネルを表示する時に使います
使用できるプロパティは以下の通り

property|type|description|option|option_description|example
---|---|---|---|---|---
layer
size
anchor_from
anchor_to
offset
grid_position
bindings
min_size
max_size
variables
ignored
clip_state_change_event
visible
ttsSectionContainer
focus_container
use_last_focus
focus_navigation_mode_down
focus_navigation_mode_up
focus_navigation_mode_right
focus_navigation_mode_left
clips_children
factory
use_anchored_offset
property_bag
inherit_max_sibling_height
priority
alpha
focus_wrap_enabled
focus_container_custom_right
focus_container_custom_up
allow_clipping
collection_index
propagate_alpha
disable_anim_fast_forward
focus_container_custom_left
enabled


### stack_panelプロパティ一覧  
**"type":"stack_panel"**  
  
使用できるプロパティは以下の通り


property|type|description|option|option_description|example
---|---|---|---|---|---
anchor_from
anchor_to
size
orientation
bindings
offset
layer
factory
min_size
collection_name
variables
use_child_anchors
visible
max_size
use_anchored_offset
property_bag
alpha
propagate_alpha
ignored
focus_container
use_last_focus
focus_navigation_mode_right
use_priority
focus_wrap_enabled
focus_navigation_mode_left
focus_container_custom_left
priority
focus_navigation_mode_down
focus_navigation_mode_up
ttsSectionContainer
enabled
clip_state_change_event


### input_panelプロパティ一覧  
**"type":"input_panel"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
size
modal
layer
button_mappings
offset
focus_container
use_last_focus
focus_identifier
tts_name
tts_control_header
bindings
anchor_from
anchor_to
focus_navigation_mode_down
focus_navigation_mode_up
focus_navigation_mode_right
focus_navigation_mode_left
gesture_tracking_button
always_handle_controller_direction
focus_enabled
always_listen_to_input
ttsSectionContainer
ignored
variables
property_bag
inline_modal
visible
focus_wrap_enabled
focus_container_custom_left
tts_skip_message
tts_skip_children
default_focus_precedence
tts_ignore_count
consume_hover_events
focus_change_down
focus_change_up
focus_change_left
focus_change_right
focus_magnet_enabled
hover_enabled
prevent_touch_input

### gridプロパティ一覧  
**"type":"grid"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
size
anchor_from
anchor_to
grid_dimensions
grid_rescaling_type
maximum_grid_items
collection_name
grid_item_template
offset
layer
grid_dimension_binding
bindings
grid_fill_direction
variables
property_bag
ttsSectionContainer
clip_state_change_event
focus_identifier

### factoryプロパティ一覧  
**"type":"factory"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
control_ids
size
control_name

### customプロパティ一覧  
**"type":"custom"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
renderer
size
anchor_to
anchor_from
property_bag
end_event
bindings
layer
rotation
use_selected_skin
animation_reset_name
anims
offset
text_color
background_color
color1
color2
ignored
use_skin_gui_scale
use_player_paperdoll
enable_scissor_test
variables
camera_tilt_degrees
starting_rotation
use_uuid
alpha
primary_color
visible
allow_clipping'

### buttonプロパティ一覧  
**"type":"button"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
size
bindings
button_mappings
layer
anchor_from
anchor_to
default_control
hover_control
pressed_control
focus_enabled
ignored
focus_identifier
focus_change_down
focus_change_up
focus_change_left
focus_change_right
focus_wrap_enabled
focus_magnet_enabled
sound_name
sound_volume
sound_pitch
default_focus_precedence
offset
locked_control
enabled
consume_event
tts_name
tts_control_header
tts_section_header
tts_control_type_order_priority
tts_index_priority
follows_cursor
always_handle_pointer
visible

### selection_wheelプロパティ一覧  
**"type":"selection_wheel"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
slice_count
inner_radius
outer_radius
focus_enabled
select_button_name
hover_button_name
analog_button_name
iterate_left_button_name
iterate_right_button_name
initial_button_slice
default_focus_precedence
tts_name
tts_control_header
tts_section_header
tts_control_type_order_priority
tts_skip_message
layer
sound_name
sound_volume
sound_pitch
state_controls
button_mappings
property_bag
bindings
size

### screenプロパティ一覧  
**"type":"screen"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
size
button_mappings
cache_screen
variables
vr_mode

### scroll_viewプロパティ一覧  
**"type":"scroll_view"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
size
offset
anchor_from
anchor_to
scroll_speed
scrollbar_track_button
scrollbar_touch_button
touch_mode
always_listen_to_input
always_handle_pointer
always_handle_scrolling
scrollbar_track
scrollbar_box
scroll_content
scroll_view_port
scroll_box_and_track_panel
jump_to_bottom_on_update
button_mappings
bindings

### toggleプロパティ一覧  
**"type":"toggle"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
focus_identifier
focus_change_down
focus_change_up
focus_change_left
focus_change_right
focus_enabled
focus_magnet_enabled
default_focus_precedence
layer
sound_name
sound_volume
sound_pitch
checked_control
unchecked_control
checked_hover_control
unchecked_hover_control
checked_locked_control
unchecked_locked_control
checked_locked_hover_control
unchecked_locked_hover_control
radio_toggle_group
toggle_name
toggle_default_state
toggle_group_forced_index
toggle_group_default_selected
toggle_grid_collection_name
enable_directional_toggling
toggle_on_button
toggle_off_button
tts_toggle_on
tts_toggle_off
tts_name
tts_control_header
tts_section_header
tts_override_control_value
tts_control_type_order_priority
tts_index_priority
tts_inherit_siblings
button_mappings
property_bag
bindings

### carousel_labelプロパティ一覧  
**"type":"carousel_label"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
shadow
color
text
always_rotate
rotate_speed
hover_color
hover_alpha
pressed_color
pressed_alpha
button_mappings

### slider_boxプロパティ一覧  
**"type":"slider_box"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
laye
size
anchor_to
anchor_from
default_control
hover_control
locked_control
indent_control

### sliderプロパティ一覧  
**"type":"slider"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
focus_identifier
focus_change_down
focus_change_up
focus_change_left
focus_change_right
focus_enabled
default_focus_precedence
slider_select_on_hover
layer
always_listen_to_input
always_handle_pointer
slider_box_control
slider_name
slider_track_button
slider_direction
slider_steps
slider_collection_name
default_control
hover_control
background_control
background_hover_control
progress_control
progress_hover_control
tts_control_header
tts_section_header
tts_override_control_value
tts_name
tts_value_changed
slider_small_decrease_button
slider_small_increase_button
slider_selected_button
slider_deselected_button
factory
button_mappings
property_bag
bindings

### dropdownプロパティ一覧  
**"type":"dropdown"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
anchor_from
anchor_to
dropdown_name
dropdown_content_control
dropdown_area
tts_control_type_order_priority

### edit_boxプロパティ一覧  
**"type":"edit_box"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
focus_identifier
focus_change_down
focus_change_up
focus_change_left
focus_change_right
focus_enabled
anchor_from
anchor_to
layer
enabled
text_box_name
text_edit_box_grid_collection_name
tts_name
tts_control_header
tts_section_header
tts_override_control_value
bindings
locked_control
default_control
hover_control
pressed_control
max_length
text_type
virtual_keyboard_buffer_control
text_control
place_holder_control
button_mappings

### scroll_trackプロパティ一覧  
**"type":"scrool_track"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
button_mappings

### scrollbar_boxプロパティ一覧  
**"type":"scrollbar_box"**  
  
使用できるプロパティは以下の通り
property|type|description|option|option_description|example
---|---|---|---|---|---
anchor_to
anchor_from
layer
visible
contained
draggable
button_mappings

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
easing|string|動作しない模様|linear推奨||
next|string|次に再生するアニメーション|@namespace.name||
resettable|bool||true<br>flase
reversible|bool|幅まで表示したときに折り返す|true<br>false|折り返す<br>始めに戻る
duration|string|アニメーションをする時間|number

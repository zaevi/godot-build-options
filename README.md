# Godot-Build-Options

用于精简优化Godot构建大小的选项清单中文对照

不建议将文件命名为`custom.py`, 因为Godot库会自动忽略此文件;

建议编译时手动指定选项清单`profile=options.py`;

因为部分模块必须要在编辑器中开启, 所以你应该维护并使用两份选项清单, 例如:

```powershell
# 构建编辑器
scons p=windows tools=yes profile=options.editor.py

# 构建导出模板
scons p=windows tools=no target=release_debug profile=options.template.py
```

详情请参考: https://docs.godotengine.org/en/latest/development/compiling/optimizing_for_size.html

## 中文参照

3D相关
|选项|说明||
|--|--|--|
|`disable_3d="no"`| 禁用3D.|仅模板可关|
|`module_gridmap_enabled = "yes"`|启用3D网格地图||
|`module_csg_enabled = "yes"`|启用构造实体几何(非破坏性布尔运算)||
|`module_bullet_enabled = "yes"`|启用Bullet物理引擎||

2D相关
|选项|说明||
|--|--|--|
|`module_freetype_enabled = "yes"`|支持使用FreeType库来动态渲染字体||
|`disable_advanced_gui = "no"`|关闭高级GUI. 禁用后相关代码依旧编译, 只是不注册至ClassDB中了|仅模板可关|
|`module_opensimplex_enabled = "yes"`|支持使用OpenSimplexNoise库生成噪点/法向贴图||
|`module_etc_enabled = "yes"`|支持加载etc1格式(.pkm)的压缩纹理, 加载得到ImageTexture|仅编辑器有效|
|`module_dds_enabled = "yes"`|支持加载DirectDraw Surface(.dds)图像||
|`module_hdr_enabled = "yes"`|支持加载高动态范围(.hdr)图像||
|`module_jpg_enabled = "yes"`|支持加载JPG/JPEG图像||
|`module_tga_enabled = "yes"`|支持加载TGA图像||
|`module_tinyexr_enabled = "yes"`|支持加载EXR图像||
|`module_webp_enabled = "yes"`|支持加载WebP图像||
|`module_bmp_enabled = "yes"`|支持加载BMP格式图像||

音视频相关
|选项|说明||
|--|--|--|
|`module_minimp3_enabled = "yes"`|支持播放MP3格式音频||
|`module_ogg_enabled = "yes"`|启用Ogg相关库, 如果要开启以下5个模块中任意一个, 都需要先启用此模块||
|`module_stb_vorbis_enabled = "yes"`|支持播放Ogg格式音频||
|`module_theora_enabled = "yes"`|支持播放OggTheora(.ogv)视频||
|`module_webm_enabled = "yes"`|支持播放WebM视频, 需要开启以下两个模块的至少一个||
|`module_vorbis_enabled = "yes"`|支持播放WebM(VP8编码)视频||
|`module_opus_enabled = "yes"`|支持播放WebM(VP9编码)视频||

网络相关
|选项|说明||
|--|--|--|
|`module_jsonrpc_enabled = "yes"`|启用JSON-RPC||
|`module_websocket_enabled = "yes"`|启用WebSocket||
|`module_mbedtls_enabled = "yes"`|支持HTTPS, 编辑器禁用后, AssetLib将会无法工作||
|`module_enet_enabled = "yes"`|支持ENet网络操作库||
|`module_upnp_enabled = "yes"`|启用UPnP, 用于网络发现或端口映射||

系统特性相关
|选项|说明||
|--|--|--|
|`module_gdscript_enabled = "yes"`|启用GDScript脚本||
|`module_visual_script_enabled = "yes"`|启用可视化脚本||
|`module_gdnative_enabled = "yes"`|支持加载GDNative库||
|`module_regex_enabled = "yes"`|启用正则表达式库||
|`module_mono_enabled = "no"`|启用Mono(C#)支持||
|`minizip = "yes"`|启用zip操作库, 禁用后将无法加载zip资源包(导出zip包正常工作)||
|`module_mobile_vr_enabled = "yes"`|启用移动端VR支持||
|`module_camera_enabled = "yes"`|启用摄像头支持||

其它
|选项|说明||
|--|--|--|
|`optimize = "size"`|编译时的优化方式, 默认为speed(Wasm下为size)|可选none/speed/size|
|`deprecated = "yes"`|禁用一些已弃用的代码, 具体请在源码中搜DISABLE_DEPRECATED标志||

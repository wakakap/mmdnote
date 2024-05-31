
记录一下此次使用过程，参考：https://www.youtube.com/watch?v=fl8m6V9Z2Pw，中间有些细节被省略，自己尝试时遇到些问题。

目录结构：
```
├── MMD_genshin_project
│ ├── Manashiku
│ │ ├── fulina - body.fx
│ │ ├── fulina - face.fx
│ │ ├── fulina - dress.fx
│ │ ├── fulina - hair.fx
│ │ ├── sub
│ │ │ ├── tex
│ │ │ │ ├── Avatar_Loli_Tex_FaceLightmap.png
│ │ │ │ ├── Avatar_Boy_Tex_FaceLightmap.png
│ │ │ │ ├── Avatar_Girl_Tex_FaceLightmap.png
│ │ │ │ ├── ...
│ ├── PmxEditor_0273
│ │ ├── _plugin
│ │ │ ├── genshin_tool
│ │ │ │ ├── MMDGenshin_Material_Gen_v1.1.6.dll
│ │ │ │ ├── MMDGenshin_Helper_V2.dll
│ ├── 芙宁娜
│ │ ├── shading
│ │ │ ├── Materials
│ │ │ │ ├── Avatar_Girl_Sword_Funingna_Mat_Body.json
│ │ │ │ ├── Avatar_Girl_Sword_Funingna_Mat_Dress.json
│ │ │ │ ├── Avatar_Girl_Sword_Funingna_Mat_Face.json
│ │ │ │ ├── Avatar_Girl_Sword_Funingna_Mat_Hair.json
│ │ │ ├── Avatar_Girl_Sword_Funingna_Tex_Body_Lightmap.png
│ │ │ ├── Avatar_Girl_Sword_Funingna_Tex_EffectHair_Lightmap.png
│ │ │ ├── Avatar_Girl_Sword_Funingna_Tex_Hair_Lightmap.png
│ │ │ ├── Avatar_Girl_Sword_Funingna_Tex_Hair_Shadow_Ramp.png
│ │ │ ├── Avatar_Girl_Sword_Funingna_Tex_Body_Shadow_Ramp.png
│ │ │ ├── ...
│ │ ├── 【芙宁娜_荒】.pmx
│ │ ├── 【芙宁娜_荒】gai.pmx
│ │ ├── 【芙宁娜_荒】gaigai.pmx
```
步骤：
- https://docs.google.com/spreadsheets/d/1lrE5EGtuDsrwRJNSHIEN9hsGggxzLHmDV5rwuHkmndQ/edit#gid=0 下载官方模型furina。https://github.com/Manashiku/MMDGenshintex 下载放在Manashiku 中。角色的shading文件下载：https://github.com/zeroruka/GI-Assets/tree/main/Models/Characters。按如上结构整理文件夹。
- 在 PmxEditor 中打开`【芙宁娜_荒】.pmx`，在素材中，看每个部分使用的 tex ，在 shading 中找对应的 `Lightmap.png` 和 `Shadow_Ramp.png`，填到sph和toon中。这个部分存在一些细节。视频里没有讲。对每个部分重命名是为了之后操作批量快速，不用一一确认。保存生成 `【芙宁娜_荒】gai.pmx`
  - 除了脸部使用乘算，其他的都选择subtex。什么意思，未知。
  - 对于这个模型，似乎编号20（腿）的sph虽然选择的是`Tex_Body_Lightmap.png`，但 toon 选择 `Hair_Shadow_Ramp.png`而不是 `Body_Shadow_Ramp.png`，否则效果上阴影颜色不对。
  - 具体细节待补充。
- PmxEditor 中，编辑-plugin，运行 `MMDGenshin_Helper_V2.dll`，全勾选，依次点击能点击的按钮，关闭。运行 `MMDGenshin_Material_Gen_v1.1.6.dll`，点击go，选择 `Avatar_Girl_Sword_Funingna_Mat_Body.json`，会选择保存地点，保存到 `fulina - body.fx`。其他对应同理。做完后关闭。保存生成`【芙宁娜_荒】gaigai.pmx`。
  - `fulina - body.fx`会调用 sub/tex 中的内容，目前github上 https://github.com/Manashiku/MMDGenshintex 的 sub/tex 中并没有内容，一些教程里的文件会带有这些。我还没搞懂具体的关系。
- 在mmd中打开改后模型。effect中对应选择fx。如果线条粗细不对，可复制fx修改里面的outline参数，根据需要应用。

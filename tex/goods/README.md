# 货品贴图覆盖目录

这里的程序化包装图是兜底。想让商品真的像便利店货架，用本地 ComfyUI 出图丢进来即可。

## 怎么用

1. 生成一张**方图**（512×512 或 768×768），正面平铺的包装设计
2. 按下面表格里的**文件名**保存为 PNG
3. 放进这个目录（`public/tex/goods/`）
4. 刷新页面 —— 有同名文件的自动替换，没有的继续用程序化版本

不用改任何代码。删掉文件就退回程序化版本。

## 文件名

| 文件名 | 品类 | 品牌（虚构） | 主色 |
|---|---|---|---|
| `lemon-tea.png` | 罐 330ml | 維樂檸茶 | 黄 `#e0b321` / 绿字 |
| `cola.png` | 罐 330ml | 可樂汽水 | 红 `#b8232b` / 白飘带 |
| `beer.png` | 罐 330ml | 嘉力啤酒 | 墨绿 `#1f5c3a` / 金 |
| `oolong.png` | 罐 500ml | 烏龍茶 | 米 `#cfc5a8` / 褐 |
| `water.png` | 瓶 500ml | 純淨水 | 淡蓝 `#cfe3f0` |
| `soymilk.png` | 瓶 250ml | 維他豆奶 | 米黄 `#f0e2b8` |
| `yakult.png` | 瓶 100ml | 益菌多 | 粉白 `#f5e6ec` |
| `cig.png` | 盒 | 紅雙喜 | 米白 `#f0ece2` / 深红 |
| `biscuit.png` | 盒 | 消化餅 | 土黄 `#d9a44e` |
| `medoil.png` | 盒 | 保心安油 | 红 `#c0392b` / 金 |
| `chips.png` | 袋 85g | 脆片 | 橙 `#e08a2c` |
| `noodle.png` | 袋 100g | 鮮湯麵 | 红 `#c0392b` / 黄 |
| `bread.png` | 袋 400g | 方包 | 米 `#e8d9b0` |
| `cupnoodle.png` | 杯 65g | 杯麵 | 米白 `#f0e8d8` / 红 |
| `yogurt.png` | 杯 120g | 乳酪 | 淡蓝 `#e8f0f8` |

## ComfyUI 提示词模板

**正向**（以柠檬茶为例，其余替换方括号里的内容）：

```
flat product packaging label design, front view, straight-on orthographic,
a slim beverage can label for [lemon tea], [golden yellow] background with
[deep green] accents, large bold typography block at top, lemon slice graphic
in the center, nutrition facts panel, barcode at bottom left, net weight text
bottom right, small print lines, printed halftone dot texture, faint plastic
film sheen, high contrast, fills entire frame
```

**负向**：

```
3d render, perspective, angled, drop shadow, reflection on floor, hands,
table surface, background scene, room, blurry, low contrast, watermark,
cropped edges
```

关键就三条：
- `flat` + `front view` + `orthographic` —— 别让它出立体效果图
- `fills entire frame` —— 否则四周留白，贴到罐子上会看到空边
- `barcode` + `nutrition facts` + `small print` —— 这三样是"像真包装"的关键，缺了就还是色块

## 尺寸

方图即可（512 或 768）。非等比会被拉伸变形。

罐和瓶是圆柱贴图，图案会绕一圈接缝，所以**左右边缘要能接上**——出图时避开左右贴边的文字。
